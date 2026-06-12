---
title: "Begginers HOW TO"
date: 2005-12-25
forum: Gaming &amp; Leisure
---

### Post by TudorB on 2005-12-25
Is there a HOW TO for the begginer level on how to set up games under Kubuntu? A step by step one?

---

### Post by Sutekh on 2005-12-25
What sort of games fo you want?

There is a package that will install a heap of KDE games
```
sudo apt-get install kdegames
```

Is there is a particular game you want to install?

Here is a good guide for installing software in general (which can include games)
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by TudorB on 2005-12-26
I was reffering to windows games, like Warcraft III, etc.

---

### Post by siempae on 2005-12-26
I am messing around with that now.  Try Cedega (its a paid program) or wine.  I have HL2 running great with Cedega.

---

### Post by TudorB on 2005-12-26
Is there a free / non commercial way to do this?

---

### Post by Sutekh on 2005-12-26
Wine is the free /non commercial way to run Windows games in Ubuntu

You'll need to add a repository to get it, using apt-get
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo kedit /etc/apt/sources.list
```
or you can use kate (or any text editor) instead of kedit

Then add this repository
```
## wine
deb http://wine.sourceforge.net/apt/ binary/

```
Then you can install with apt-get from the command line or Synaptic or Adept
```
sudo apt-get install wine
```
Once you've installed wine run
```
winecfg
```
To setup the configuration

Probably the most important thing to set in winecfg is the cdrom drives
Click the 'Drives' tab, and choose autodetect.  Then select the drive which is your cdrom drive, it will have the path /media/cdrom0 or similar.  Then click the 'show advanced' tab and choose 'CD-ROM' in the type box.

To install a game use the wine command
```
wine /path/to/game/installer.exe
```

---

### Post by jsteve54302 on 2005-12-26
[new poster]  I just tried this, and got this result:

> john@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate


I get the same after running sudo apt-get update and retrying.  Have the wine binaries been removed from all the servers, or what?

---

### Post by Stealth on 2005-12-26
Does: **sudo apt-get update** give any errors?

---

### Post by jsteve54302 on 2005-12-26
No - here's the full output:

j> ohn@ubuntu:~$ sudo apt-get update
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Fetched 19.8kB in 12s (1598B/s)
Reading package lists... Done

May there just aren't any binaries or sources for ubuntu 5.10 on amd64?  I've even gone to the sourceforge site and followed their instructions, with exactly the same result.  The packages just don't seem to exist on the servers...

---

### Post by Sutekh on 2005-12-26
[QUOTE=jsteve54302]No - here's the full output:
May there just aren't any binaries or sources for ubuntu 5.10 on amd64?  I've even gone to the sourceforge site and followed their instructions, with exactly the same result.  The packages just don't seem to exist on the servers...[/QUOTE]
Oh you're on AMD64, well there's a problem to begin with.
It can be done, but you'll need to do some searching.  There was something I read once about installing the debian wine package using --force-architecture.
But I don't really know anything about it.

---

### Post by jsteve54302 on 2005-12-26
Ok...  I got the sources downloaded with sudo apt-get source wine, but when I compile them with sudo apt-get --build source wine, I get the following:

> john@ubuntu:~$ sudo apt-get --build source wine
Reading package lists... Done
Building dependency tree... Done
Need to get 13.2MB of source archives.
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.3-winehq-1 (dsc) [1137B]
Get:2 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.3-winehq-1 (tar) [13.1MB]
Get:3 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ wine 0.9.3-winehq-1 (diff) [46.2kB]
Fetched 3B in 0s (3B/s)
Skipping unpack of already unpacked source in wine-0.9.3-winehq
dpkg-buildpackage: source package is wine
dpkg-buildpackage: source version is 0.9.3-winehq-1
dpkg-buildpackage: source changed by Scott Ritchie <scott@open-vote.org>
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-buildpackage: host architecture amd64
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-checkbuilddeps: Unmet build dependencies: flex bison libicu28-dev libncurses5-dev libungif4-dev | giflib3g-dev libjack0.80.0-dev libcapi20-dev docbook-utils fontforge libldap2-dev libxxf86vm-dev libxxf86dga-dev prelink libsane-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command 'cd wine-0.9.3-winehq && dpkg-buildpackage -b -uc' failed.
E: Child process failed


Do I need to reinstall gcc or something?  Also, it says it needs to download 13+ MB, but the whole thing only takes a couple seconds.  Even at DSL, downloads aren't _that_ fast...

---

### Post by strikeforce on 2005-12-27
You need to install the build dependancies that are listed and then you need to export cc=gcc3.4 or cc=gcc4.0 whatever it is.

---

### Post by jsteve54302 on 2006-01-08
[QUOTE=strikeforce]You need to install the build dependancies that are listed and then you need to export cc=gcc3.4 or cc=gcc4.0 whatever it is.[/QUOTE]

I've satisfied the dependencies, but I'm now getting an error stating that "gcc cannot create an executable".  Since I have no problem compiling a simple "hello world" program with this user, and executing the output with expected results, I'm assuming that there is something buried in the make code or source that's causing gcc to barf...  I've noticed that the build uses (and insists on using) gcc -m32, where I need it to use gcc -m64.  I've tried to find the correct make/m4/whatever file, but seem to keep missing the appropriate lines...  A master programmer I am not, and I start going cross-eyed after about 1000 lines of code.  Could somebody point me in the right direction?  And should I maybe move this to a programming forum, even though it's wine-specific?

BTW, I haven't seen any activity from the original poster...  Has their problem been solved?

---

