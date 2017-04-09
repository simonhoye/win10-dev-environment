# win10-dev-environment

## Ubuntu Linux on Windows

 * Ensure that you're running Windows 10 Anniversary Update (build 14311 and up)
 * Enable Developer Mode (Settings - Update & security > For developers)
 * Search for “Windows Features” and choose “Turn Windows features on or off” and enable Windows Subsystem for Linux (Beta).
 * To get Bash installed, open Command Prompt and type “bash”
 
## The Goods
 * [Package Management](#package-management-chocolatey)
 * [Terminal](#terminal-cmder-with-powershell-support)
 * [Bash Tools](#bash-tools-wget-curl-etc-gow)
 * [Node.js](#node)
 * [npm](#npm)
 * [yarn](#yarn)
 * [Git](#git)
 * [Atom, Sublime, VS Code](#code-editors-atom-sublime-vs-code)
 * [Ruby](#ruby)
 * [Go](#go)
 * [Python](#python)
 * [Docker](#docker)
 * [SSH](#ssh)
 * [Azure Cli](#azure-cli)
 * [AWS Cli](#aws-cli)
 * [Basic Tools](#basic-tools)

#### Package Management: Chocolatey
Chocolatey is a powerful package manager for Windows, working sort of like apt-get or homebrew. Let's get that first. Fire up CMD.exe as Administrator and run:

```
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```

Once done, you can install packages by running `cinst` (short for `choco install`). Most packages below will be installed with Chocolatey.

###### Bonus: Use Windows 10 & OneGet
Windows 10 comes with [OneGet](https://github.com/OneGet/oneget), a universal package manager that can use Chocolatey to find and install packages. To install, run:

```
Get-PackageProvider -name chocolatey
```

Once done, you can look for all Chrome packages by typing `Find-Package -Name Chrome` or install it by typing `Install-Package -Name GoogleChrome`.

#### Terminal: CMDer (with PowerShell Support)
The PowerShell in Windows 10 got a bunch of upgrades, but it's even better if used with [CMDer](https://github.com/bliker/cmder/) or [Hyper](https://hyper.is/), both poweful toosl to do more command-line things with. CMDer is the old-school veteran, while Hyper hasn't been around for long. Try both and see what you like more! Install with:

```
cinst cmder -pre
cinst hyper
```

Even if you don't want to use CMDer, you should enable your PowerShell to execute scripts. You're a developer - the terminal is your friend.

```
Set-ExecutionPolicy Unrestricted -Scope CurrentUser
```

#### Bash Tools (wget, curl, etc): Gow
If you're coming from a Unix machine, you might miss commands like curl, diff, grep and many other. Gow is your friend - it's a collection of a 100+ famous Unix tools recompiled for Windows.

```
cinst Gow
```

#### Node
A bunch of tools are powered by Node and installed via npm. This applies to you even if you don't care about Node development. If you want to install tools for React, Azure, TypeScript, or Cordova, you'll need this.

```
cinst nodejs.install
```

#### NPM
You just installed Node, which means that you also installed a slightly outdated version of npm. npm@3 is currently in development and offers a bunch of benefits for Windows users. You probably want to upgrade to npm@3.

```
npm install -g npm-windows-upgrade
npm-windows-upgrade
```

#### Yarn
Yarn looks to be a more reliable and secure package manager than npm
```
npm install -g yarn
```

#### Version Control: Git
Obviously. If you want Git to be able to save credentials (so you don't have to enter SSH keys / passwords every single time you do anything), also install the Git Credential Manager for Windows.

```
cinst git.install
cinst poshgit

# Restart PowerShell / CMDer before moving on - or run
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")

cinst Git-Credential-Manager-for-Windows
cinst github
```

#### Code Editors: Atom, Sublime, VS Code

```
cinst SublimeText3
cinst sublimetext3-contextmenu
cinst SublimeText3.PackageControl
cinst SublimeText3.PowershellAlias

cinst Atom
cinst visualstudiocode
```

##### Visual Studio 2017

```
cinst visualstudio2017community
```

#### Ruby

```
cinst ruby
cinst ruby.devkit
```

#### Go
```
cinst golang
```

#### Python

```
cinst python
cinst pip
cinst easy.install
````

#### Docker

```
cinst docker-for-windows
```

#### Azure Cli

```
npm install -g azure-cli
```

#### AWS Cli

```
cinst awscli
cinst awstools.powershell
```

### Basic Tools

```
cinst 7zip.install
cinst sysinternals
cinst DotNet3.5
```
