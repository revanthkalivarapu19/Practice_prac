# SE Lab — Git, GitHub, Docker & Maven Quick Reference

> Every command and step below is taken **only** from the college-provided materials:
> `Git  GitHUB.pdf`, `Git with Local Repository.docx`, `Git with Remote repository.docx`,
> `Docker file, Single containerization.docx`, and `Maven Java and Web Projects.docx`.
> Each heading is a command (or a step), and beside it is what it does.

---

## 1. Git — Version & Configuration

### `git --version` (or `git version`) — Displays the installed Git version.
### `git config --global user.name "Your Name"` — Sets the author name used for all commits.
### `git config --global user.email "youremail@example.com"` — Sets the author email used for all commits.
### `git config --list` — Displays all the Git configurations for the current user.
### `git help <command>` — Shows the documentation/manual for a Git command (e.g. `git help add`).

---

## 2. Git — Repository Management & Remotes

### `git init` — Initializes a new Git repository in the current directory (creates the `.git` folder).
### `git clone <url>` — Creates a local copy of an existing remote (GitHub) repository.
### `git remote -v` — Shows the remote repositories connected to your local repository.
### `git remote add origin <url>` — Adds a new remote repository under the name `origin`.
### `git remote remove <remote_name>` — Removes a remote repository from your local configuration.
### `git remote rename <old_name> <new_name>` — Renames an existing remote.
### `git remote set-url <remote_name> <new_url>` — Changes the URL of an existing remote.
### `git remote show <remote_name>` — Shows detailed information about a remote repository.
### `git remote prune origin` — Removes remote-tracking references for branches already deleted on the remote.

---

## 3. Git — Staging, Committing & Push/Pull

### `git status` — Shows the state of the working directory and staging area (untracked/modified/staged files).
### `git add <file>` — Stages a specific file into the index.
### `git add .` — Stages all changes in the current directory.
### `git commit -m "message"` — Saves the staged changes to the local repository with a message.
### `git commit` — Commits staged changes (used while completing a merge).
### `git commit --amend -m "Corrected commit message"` — Corrects the message of the last (unpushed) commit.
### `git push <remote_name> <branch_name>` — Pushes local commits to a remote repository (e.g. `git push origin main`).
### `git push -u origin master` — Pushes to the `master` branch and sets upstream tracking.
### `git push -u origin main` — Pushes to the `main` branch and sets upstream tracking.
### `git push --set-upstream <remote_name> <branch_name>` — Pushes for the first time and sets the upstream branch.
### `git pull <remote_name> <branch_name>` — Fetches the latest remote changes and merges them into your branch (e.g. `git pull origin main`).

---

## 4. Git — Branching & Merging

### `git branch` — Lists all local branches.
### `git branch -a` — Lists all branches (local and remote).
### `git branch -r` — Lists all remote branches.
### `git branch <branch-name>` — Creates a new branch.
### `git branch -d <branch_name>` — Deletes a branch (use `-D` to force-delete if not merged).
### `git branch --merged` — Lists branches that are already merged into the current branch (safe to delete).
### `git branch -d branch1 branch2 branch3` — Deletes multiple local branches at once.
### `git checkout <branch-name>` — Switches to an existing branch.
### `git checkout -b <new-branch>` — Creates a new branch and switches to it immediately.
### `git checkout main` — Switches to the `main` branch.
### `git merge <branch-name>` — Merges the specified branch into the current branch.
### `git merge main` — Merges `main` into the current branch (used to keep a feature branch updated).
### `git fetch <remote_name>` — Downloads remote updates without merging them into your branch.
### `git fetch <remote_name> <branch_name>` — Fetches a specific branch from a remote (e.g. `git fetch origin feature-branch`).
### `git fetch origin` — Downloads the latest remote changes without merging.
### `git rebase <remote_name>/<branch_name>` — Rebases your local branch onto a remote branch to keep linear history (e.g. `git rebase origin/main`).

---

## 5. Git — Undo, History & Recovery

### `git reset <file>` — Removes a file from the staging area but leaves the working directory unchanged.
### `git reset --hard` — Resets the working directory and staging area to the last commit.
### `git revert <commit>` — Creates a new commit that undoes a specified commit, leaving history intact.
### `git log` — Shows the commit history (hashes, messages, timestamps).
### `git log --oneline` — Shows a concise one-line view per commit.
### `git diff` — Shows changes not yet staged (working directory vs staging area).
### `git show <commit>` — Shows the details of a specific commit, including changes and message.
### `git restore <filename>` — Discards uncommitted changes to a file, restoring it to the last commit.
### `git reflog` — Records every HEAD movement; used to recover lost commits/branches.
### `git checkout -b <branch_name> <commit_hash>` — Recreates a deleted branch from a commit found in `git reflog`.
### `git stash` — Saves uncommitted changes and reverts to a clean state.
### `git stash apply` — Restores the stashed changes.
### `git blame <file>` — Shows who last changed each line of a file (e.g. `git blame script.py`).
### `git filter-branch --force --index-filter "git rm --cached --ignore-unmatch secrets.txt" --prune-empty --tag-name-filter cat -- --all` — Removes an accidentally committed sensitive file from the entire Git history.

---

## 6. Git — .gitignore

### `touch .gitignore` — Creates a `.gitignore` file in the project root.
### `*.log` — Ignores all `.log` files.
### `secret_file.txt` — Ignores a specific file.
### `temp/` — Ignores all files in a `temp/` directory.
### `folder/*` followed by `!folder/important_file.txt` — Ignores everything in a folder except one file.
### `*.bak` — Ignores files with a specific extension.

---

## 7. Git — Patches (create & apply)

### `git format-patch -1 <commit-hash>` — Creates a `.patch` file from one commit (e.g. `git format-patch -1 abc1234`).
### `git format-patch -3` — Creates patch files for the last 3 commits.
### `git format-patch <base_commit>..HEAD` — Creates patches for a range of commits.
### `git apply <file.patch>` — Applies a patch file to the working tree (e.g. `git apply my-changes.patch`).
### `git am <file.patch>` — Applies a patch made by `git format-patch` and recreates the original commit.

---

## 8. Git — Merge Conflict Resolution

### `git status` — Shows which files are in conflict (marked `both modified`).
### `<<<<<<< HEAD` … `=======` … `>>>>>>> branch` — Conflict markers inside the file; `HEAD` is your version, the lower section is the other branch.
### `git add <file>` — Marks the resolved (edited) file as resolved.
### `git commit` — Completes the merge commit after resolving (only if Git did not auto-create it).
### `git rebase --continue` — Continues a rebase after resolving conflicts.
### `git merge --abort` — Cancels a messy merge and returns to the state before the merge.

---

## 9. GitHub — Web Steps

### Create a repository — On github.com: click **New repository** → give it a name → choose **Public** or **Private** → **Create repository**.
### Copy the repository URL — After creating, GitHub shows the HTTPS/SSH URL to use with `git remote add origin`.
### Push an existing project — In Git Bash run `git init`, `git remote add origin <url>`, `git add .`, `git commit -m "Initial commit"`, then `git push -u origin main` (or `master`).
### Fork a repository — Open the public repo → click **Fork** (top-right); GitHub creates a copy under your account.
### Open a Pull Request — On your fork: click **Pull request** / **Contribute → Open pull request** → add title and description → **Create pull request**.
### Review a Pull Request — The owner: **Pull requests** → click the commit → **Files changed** → **Review changes** → **Submit review** → **Merge pull request** → **Confirm merge**.

---

## 10. GitHub — SSH Key Setup

### `ssh-keygen -t rsa` — Generates an SSH key pair (private key stays on your machine, public key is shared).
### Copy the public key — Open the file `id_rsa.pub` and copy its contents.
### Add to GitHub — GitHub → **Settings → SSH and GPG keys → New SSH key** → paste the key → **Add SSH key**.

---

## 11. GitHub — Collaboration (Organization, Collaborators, Fork, PR)

### Create a free organization — GitHub → **New organization → Create a free organization** → enter name, email, verification → **Next**.
### Add members — During setup, add members; invitations are sent and must be accepted.
### Set base permissions — GitHub → **Settings → Member privileges → Base permissions → Write**, and **Projects base permissions → Write**.
### Create a shared organization repository — In the organization, create the repository that all members can access.
### Add a collaborator (Collaborator 1) — Repo → **Settings → Collaborators → Manage Access → Add people** → search and add; the invitation is sent.
### Accept the invitation (Collaborator 2) — Open the email/GitHub notification and click **Accept invitation**.
### Collaborator 2 setup and workflow — `git config --global user.name`, `git config --global user.email`, `git remote -v`, `git clone <url>`, `cd <repo>`, `git checkout -b feature/your-feature-name`, `git add .`, `git commit -m "message"`, `git push origin feature/your-feature-name`.
### Keep a branch updated — `git checkout main`, `git pull origin main`, `git checkout feature/your-new-feature`, `git merge main`.
### Fork workflow — **Fork** the public repo → clone your fork → `git add .` → `git commit` → `git push origin main` → open a **Pull Request** back to the original repo.
### Sync a fork / keep updated — `git checkout main`, `git pull origin main`, `git checkout feature/your-new-feature`, `git merge main`.

---

## 12. Docker — Concepts

### Docker Image — A read-only template containing the application code, runtime, libraries and dependencies (a blueprint).
### Docker Container — A running instance of a Docker image.
### Dockerfile — A text file with instructions used to create a custom Docker image.

---

## 13. Docker — CLI Commands

### `docker pull redis` — Downloads the `redis` image from Docker Hub to your local system.
### `docker run --name my-redis -d redis` — Creates and starts a container named `my-redis` from `redis` in the background.
### `docker ps` — Lists all currently running containers.
### `docker ps -a` — Lists all containers, including stopped ones.
### `docker exec -it my-redis redis-cli` — Opens the Redis command-line tool inside the running container.
### `docker stop my-redis` — Stops the Redis container (does not delete it).
### `docker start my-redis` — Restarts the stopped container.
### `docker rm my-redis` — Deletes the container permanently (stop it first).
### `docker rmi redis` — Deletes the `redis` image from your local system.
### `docker build -t redisnew .` — Builds an image named `redisnew` from the Dockerfile in the current folder.
### `docker run --name myredisnew -d redisnew` — Starts a background container named `myredisnew` from the custom image.
### `docker stop myredisnew` — Stops the container named `myredisnew`.
### `docker login` — Logs in to your Docker Hub account so you can upload images.
### `docker commit 0e993d2009a1 budarajumadhurika/redis1` — Saves the state of the container with that ID into a new image.
### `docker images` — Lists all images saved on your system.
### `docker push budarajumadhurika/redis1` — Uploads the image to Docker Hub.
### `docker rm 0e993d2009a1` — Deletes the container with the given ID.
### `docker rmi budarajumadhurika/redis1` — Deletes the given image from your system.
### `docker logout` — Logs you out of Docker Hub and removes your stored credentials.
### `docker pull budarajumadhurika/redis1` — Downloads the given image from Docker Hub.
### `docker run --name myredis -d budarajumadhurika/redis1` — Starts a new container from the downloaded image.
### `SET name "Alice"` — Saves a key-value pair in Redis.
### `GET name` — Retrieves the value of a key from Redis.
### `exit` — Exits the Redis CLI.

---

## 14. Docker — Dockerfile

### `FROM redis:latest` — Sets the base image on which the custom image is built.
### `CMD ["redis-server"]` — Sets the default command run when the container starts.

---

## 15. Docker — Custom Image, Push & Pull Workflow (as in the lab)

### Step 1 — Create a project folder (e.g. `C:\DockerProjects\Redis`) and run `cd /c/DockerProjects/Redis` in Git Bash.
### Step 2 — Create a file named `Dockerfile` (no extension) with `FROM redis:latest` and `CMD ["redis-server"]`.
### Step 3 — `docker build -t redisnew .` — Builds the custom image.
### Step 4 — `docker run --name myredisnew -d redisnew` — Runs a container from the custom image.
### Step 5 — `docker ps` — Verifies the container is running.
### Step 6 — `docker stop myredisnew` — Stops the container.
### Step 7 — `docker login` — Authenticates with Docker Hub.
### Step 8 — `docker ps -a` — Lists all containers to retrieve the container ID.
### Step 9 — `docker commit 0e993d2009a1 budarajumadhurika/redis1` — Creates a repository image from the container snapshot.
### Step 10 — `docker images` — Confirms the new image exists.
### Step 11 — `docker push budarajumadhurika/redis1` — Uploads the image to Docker Hub.
### Step 12 — `docker rm 0e993d2009a1` — Deletes the local container.
### Step 13 — `docker rmi budarajumadhurika/redis1` — Deletes the local image.
### Step 14 — `docker ps -a` — Confirms the container is gone.
### Step 15 — `docker logout` — Logs out of Docker Hub.
### Step 16 — `docker pull budarajumadhurika/redis1` — Downloads the uploaded image again.
### Step 17 — `docker run --name myredis -d budarajumadhurika/redis1` — Starts a container from the pulled image.
### Step 18 — `docker exec -it myredis redis-cli` — Enters the container and opens Redis CLI.
### Step 19 — `SET name "Abcdef"` — Saves data inside Redis.
### Step 20 — `GET name` — Retrieves the saved data.
### Step 21 — `exit` — Exits the Redis CLI.
### Step 22 — `docker ps -a` — Checks container status.
### Step 23 — `docker stop myredis` — Stops the container.
### Step 24 — `docker rm 50a6e4a9c326` — Deletes the container by ID.
### Step 25 — `docker images` — Lists remaining images.
### Step 26 — `docker rmi budarajumadhurika/redis1` — Deletes the image again.
### Step 27 — `docker logout` — Removes stored login credentials.

---

## 16. Maven — Project Structure & Build

### `src/main/java/` — Application source code.
### `src/main/resources/` — Configuration files (e.g. `config.properties`).
### `src/test/java/` — Unit test source code.
### `src/test/resources/` — Test resources.
### `target/` — Directory where compiled files and reports are generated after a successful build.
### `mvn clean install` — `clean` deletes the previous build (`target/`); `install` builds, tests and installs the package to the local `.m2` repository.
### `~/.m2/repository/groupId/artifactId/version/` — Location where the built artifact and downloaded dependencies are stored.
### Dependency example (added in `pom.xml`):
```xml
<dependency>
  <groupId>com.google.code.gson</groupId>
  <artifactId>gson</artifactId>
  <version>2.10</version>
</dependency>
```
### After a wrong/missing dependency version — Maven reports **BUILD FAILURE** with a dependency resolution error.

---

## 17. Maven — Creating a Java Project in Eclipse (steps)

### Step 1 — Open Eclipse IDE and launch a workspace.
### Step 2 — Install the Maven plugin if needed: **Help → Eclipse Marketplace → search "Maven Integration for Eclipse" → Install**.
### Step 3 — **File → New → Project… → expand Maven → select Maven Project → Next**.
### Step 4 — Select the workspace location (default or custom) → **Next**.
### Step 5 — Choose an archetype (e.g. `org.apache.maven.archetypes → maven-archetype-quickstart 1.4`) → **Next**.
### Step 6 — Define metadata: **Group ID** (e.g. `com.example`), **Artifact ID** (e.g. `my-maven-project`), **Version** → **Finish**; type `Y` when prompted in the console.
### Step 7 — The project is created with the standard Maven layout (`src/main/java`, `src/test/java`, `pom.xml`).
### Step 8 — If needed: right-click project → **Maven → Update Project…** to refresh dependencies.
### Step 9 — Right-click `App.java` → **Run As → Maven Clean / Maven Install / Maven Test / Maven Build**.
### Step 10 — In the Maven Build dialog enter Goals: `clean install test` → **Apply → Run**.
### Step 11 — Check the console for the **BUILD SUCCESS** message.
### Step 12 — Right-click `App.java` → **Run As → Java Application**; output shows `Hello World`.

---

## 18. Maven — Creating a Web Project in Eclipse (steps)

### Step 1 — Launch Eclipse and select/create a workspace.
### Step 2 — **File → New → Project… → expand Maven → Maven Project → Next**.
### Step 3 — Choose the archetype `org.apache.maven.archetypes → maven-archetype-webapp 1.4` → **Next**.
### Step 4 — Configure **Group Id** (e.g. `com.example`) and **Artifact Id** (e.g. `my-web-app`) → **Finish**.
### Step 5 — Open `pom.xml` and add web dependencies (e.g. Servlet API), copied from `mvnrepository.com`:
```xml
<dependency>
  <groupId>javax.servlet</groupId>
  <artifactId>javax.servlet-api</artifactId>
  <version>4.0.1</version>
  <scope>provided</scope>
</dependency>
```
### Step 6 — Configure the server: **Window → Show View → Servers → Add server → Tomcat v9.0 → Next** and set ports/location.
### Step 7 — Modify `tomcat-users.xml` to add role and user details under `<tomcat-users>`.
### Step 8 — Right-click `index.jsp` → **Run As → Maven Clean / Maven Install / Maven Test / Maven Build**.
### Step 9 — In the Maven Build dialog enter Goals: `clean install test` → **Apply → Run**.
### Step 10 — Check the console for the **BUILD SUCCESS** message.
### Step 11 — Right-click `index.jsp` → **Run As → Run on Server** → select Tomcat → **Finish**.
### Step 12 — The `Hello World` web page is displayed.
### Push to GitHub — Push your Maven Java project and Maven Web project into your GitHub repository (using the Git commands in Sections 2–3).

---

## 19. Maven — Java Version, JUnit, Resources & Errors

### `maven-compiler-plugin` configuration in `pom.xml` — Sets the Java version explicitly:
```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <version>3.11.0</version>
  <configuration>
    <source>17</source>
    <target>17</target>
  </configuration>
</plugin>
```
### `mvn package` — Builds the project; inspect the generated JAR with `jar tf target/myapp.jar`.
### JUnit test file location — Place tests in `src/test/java` (annotated with `@Test` and `assertEquals`).
### `mvn test` — Compiles and runs the unit tests.
### `target/test-classes/` — Stores the compiled test `.class` files.
### `target/surefire-reports/` — Stores the `.txt`/`.xml` JUnit test results.
### Typo in version or missing repository in `pom.xml` — Causes **BUILD FAILURE**; Maven prints a precise error; fix the dependency tag and re-run `mvn clean install`.
### `src/main/resources/config.properties` — Location for configuration files.
### `InputStream input = getClass().getClassLoader().getResourceAsStream("config.properties");` — Reads a resource file from the classpath.
### `target/classes/` — After build, the resource file should exist here.

---

## 20. Maven — Multi-Module, Executable JAR & WAR

### Multi-module structure — A parent `pom.xml` (packaging `pom`) with sub-modules `core/` and `web/`, each having its own `pom.xml`.
### Parent `pom.xml` — Defines `<modules>` and common dependencies; each sub-module builds independently into its own `target/`.
### Executable JAR plugin (`maven-jar-plugin`) — Configured in `pom.xml` to set the main class:
```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-jar-plugin</artifactId>
  <configuration>
    <archive>
      <manifest>
        <mainClass>com.example.Main</mainClass>
      </manifest>
    </archive>
  </configuration>
</plugin>
```
### `mvn package` then `java -jar target/myapp.jar` — Builds and runs the executable JAR.
### WAR structure — Create `src/main/webapp/WEB-INF/web.xml` and set `<packaging>war</packaging>` in `pom.xml`.
### `mvn package` (WAR) — Generates `target/mywebapp.war`, which is deployed on a Tomcat server.
