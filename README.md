# Package-Manager
Learn About Package Manager


# What is a Package Manager?
A package manager is a tool that helps you install, update, remove, and manage software on your computer using commands instead of manually downloading and installing every application.

Think of it as an app store for your terminal.

For example, if you want to install Git on your Mac, you could download it manually or use a package manager such as Homebrew.

```
brew install git
```

The package manager finds the software, downloads it, and handles many of its dependencies automatically.

## 1. How does a package manager work?

  1. You run a command
      Example: `brew install nginx`
  
  2. Package manager searches its repository
     Finds the requested software and required dependencies.
  
  3. Downloads and installs
     Installs files and configures the package as needed.
  
  4. Software is ready to use
  
  You can run using this command - /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"


## 2. Types of package managers by operating system

Different operating systems and Linux distributions use different package managers. Some are built into the operating system; others must be installed separately.

### A. macOS (MacBook / Mac)

  1. Homebrew (`brew`)
      Recommended for developers
      Installs developer tools such as Git, Nginx, Python, Docker CLI and Node.js.
      ```
      brew install git
      brew install nginx
      brew update
      brew upgrade
      ```
  2. MacPorts (`port`)
    An alternative package manager for macOS that installs software and its dependencies.
    ```
    sudo port install git
    port selfupdate
    ```
Important: `brew` and `port` are separate package managers. Installing Homebrew does not automatically install MacPorts, or vice versa.

### B. Windows

  1. WinGet (`winget`)
    Microsoft's command-line package manager for installing and managing Windows applications.
    ```
    winget search git
    winget install --id Git.Git
    winget upgrade --all
    ```
  2. Chocolatey (`choco`)
    A popular third-party package manager for Windows.
      ```
      choco install git
      choco upgrade all
      ```
  3. Scoop (`scoop`)
    Useful for command-line tools and developer applications, often installed within your user account.
    ```
    scoop install git
    scoop update
    ```


### C. Linux

Linux has several distributions, and each may use a different package manager.

  1. APT (`apt`) — Ubuntu / Debian
    
    ```
    sudo apt update
    sudo apt install nginx
    sudo apt upgrade
    ```

 Packages commonly use the `.deb` format.
  
  2. DNF (`dnf`) — Fedora / RHEL-based systems
  
    ```
    sudo dnf install nginx
    sudo dnf upgrade
    ```
  3. Pacman (`pacman`) — Arch Linux
  
  ```
  sudo pacman -S nginx
  sudo pacman -Syu
  ```

## 3. Package managers for programming languages

One important distinction: OS package managers and programming-language package managers are not the same thing. You can use both on the same computer.

| Package manager | Used for                      | Example                              |
| --------------- | ----------------------------- | ------------------------------------ |
| `pip`           | Python libraries              | `pip install requests`               |
| `npm`           | JavaScript / Node.js packages | `npm install express`                |
| `yarn`          | JavaScript packages           | `yarn add express`                   |
| `Maven`         | Java dependencies             | `mvn install`                        |
| `Gradle`        | Java and Kotlin builds        | `gradle build`                       |
| `Cargo`         | Rust packages                 | `cargo add serde`                    |
| `NuGet`         | .NET packages                 | `dotnet add package Newtonsoft.Json` |
| `gem`           | Ruby packages                 | `gem install rails`                  |

For example, Homebrew can install Python itself, while `pip` installs Python libraries that your Python application needs.

## 4. Difference between `brew`, `port`, `sudo` and `apt`

Since you're learning package management on macOS, these distinctions are particularly useful.

| Term      | Meaning                                                              |
| --------- | -------------------------------------------------------------------- |
| `brew`    | Homebrew package manager                                             |
| `port`    | MacPorts package manager                                             |
| `apt`     | Package manager for Debian/Ubuntu Linux                              |
| `sudo`    | Runs a command with elevated privileges; it is not a package manager |
| `install` | An operation supported by many package managers                      |

For example:

```
brew install gh
```

Uses Homebrew to install GitHub CLI.

```
sudo port install gh
```

Uses MacPorts with elevated privileges to install GitHub CLI. It works only if MacPorts is installed.

```
sudo apt install gh
```

Uses APT on a compatible Linux distribution, not the native macOS terminal.

Homebrew is designed so that routine package installations generally do not require `sudo` after its initial setup.

## 5. Check which package managers are installed on your Mac

Run these commands individually in your macOS Terminal:

```
brew --version
port version
conda --version
npm --version
pip3 --version
```

If a command returns a version, that tool is available through your shell. If it says `command not found`, the tool may be absent or not configured in your `PATH`.

To check Homebrew and MacPorts locations:

```
which brew
which port
```

To see whether common package-manager executables are available:

```
command -v brew
command -v port
command -v conda
command -v npm
command -v pip3
```




###### To check, which Package Manager is installed you can use below script. 


echo "Checking package managers..."

for cmd in brew port conda mamba pip pip3 npm yarn pnpm \
          cargo go nix pkg; do
  if command -v "$cmd" >/dev/null 2>&1; then
    echo "✅ $cmd: $(command -v "$cmd")"
  else
    echo "❌ $cmd: Not found"
  fi
done
