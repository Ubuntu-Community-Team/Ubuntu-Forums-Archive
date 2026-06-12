---
title: "How to remove ubuntu 11.04 the default graphical desktop? And login to using terminal"
date: 2011-10-28
forum: Desktop Environments
---

### Post by iamtrying on 2011-10-28
Ubuntu 11.04 how can i remove the Graphical desktop environment completely?

[IMG]http://i.stack.imgur.com/3aVDq.png[/IMG]

---

### Post by nothingspecial on 2011-10-28
You would like to stop the "graphical desktop" from starting.......


.....or you would like to remove all it's components from your computer and have a commandline only system?

---

### Post by iamtrying on 2011-10-28
@nothingspecial: ".....or you would like to remove all it's components from your computer and have a commandline only system?"

Yes this i want to do. How please.

---

### Post by nothingspecial on 2011-10-28
The easiest way would be to install and run tasksel

Then uncheck ubuntu-destop

But you will have all sorts of leftover files and stuff.

The best way would be to install from the minimal cd over the top.

In both cases I would recommend that you have a wired internet connection unless you know how to configure wireless from the cli

---

### Post by iamtrying on 2011-10-28
Very good suggestion. I tried that. I boot my liveUSB.

1. I cant customize what i want to install such as you mentioned "uncheck ubuntu-destop"

2. If i start installing it ends up with GUI

How can i have a LiveCD or USB which allow me to select packages?

Link i am using 64-bit desktop: [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

---

### Post by iamtrying on 2011-10-28
1. LiveUSB boot
2. Install ubuntu selected
3. press <TAB>
> /casper/vmlinuz initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

What i may change here so that it allow me to have package selection choice?

---

### Post by nothingspecial on 2011-10-28
Download the minimal cd

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by iamtrying on 2011-10-28
@nothingspecial: I tried that too, see what i got now

[IMG]http://i.stack.imgur.com/LPzzt.png[/IMG]

---

### Post by nothingspecial on 2011-10-28
I don't understand?

---

### Post by iamtrying on 2011-10-28
@nothingspecial: According to your given link. i have tried the 64-bit desktop mini.iso's all of them and none of them has a choice where i can tell "uncheck ubuntu desktop" can you please advise? Which one you ever saw that option exists?


InstallationMinimalCD
Contents
32-bit PC (x86)
64-bit PC (amd64, x86_64)
32-bit PowerPC**
64-bit PowerPC**
Itanium (IA-64)**
Sparc**
The Minimal CD will download packages from online archives at installation time instead of providing them on the install CD itself. Downloading packages at install time reduces the size of the install CD to approximately 5 to 30MB depending on architecture (see below), as well as providing only the packages needed for installation. The download time savings achieved by using a Minimal CD can be significant, as only current packages are downloaded, so there is no need to upgrade packages immediately after installation. The Minimal CD uses a text-based installer like the Alternate CD, making the CD image as compact as possible.

To use the Minimal CD download mini.iso from one of the following links and burn it to a CD.

For help with CD burning, see BurningIsoHowto
For differences between Ubuntu release versions, please see Releases.
To install, boot your computer from the the Minimal CD and type "cli" (command line install) at the prompt. You can then follow the instructions from the text-based installer. After the base system is installed, log in, and type "sudo tasksel" to select the system to install.

32-bit PC (x86)

Ubuntu 11.10 "Oneiric Ocelot" Minimal CD 23MB (MD5: 6192789c4fad45816c07d4256cfaa24e, SHA1: 5ec65c055c409f1d88340fbe45efabe1cde64f25)
Ubuntu 11.04 "Natty Narwhal" Minimal CD 19MB (MD5: cc1591035877c317fdef7f4ebf1662b9, SHA1: d86f78c8343009e57b0ecda14592e76802ce1ec4)
Ubuntu 10.10 "Maverick Meerkat" Minimal CD 12.7MB (MD5: 02abb1a71bde21a1335e9368dad529ca, SHA1: 78086cf96c4a5578cb113d5eb218efc2573a0f82)
Ubuntu 10.04 "Lucid Lynx" Minimal CD 12.5MB* (MD5: 7b383bcf55f09b1bb7e6614ed6e67a0e, SHA1: 40ea24c2c7a5a821d37fc93d5539f2160f7e1ef6)
Ubuntu 8.04 "Hardy Heron" Minimal CD 9.8MB* (MD5: a2a3be51af1df5ba3524e764b65127b4)
64-bit PC (amd64, x86_64)

Ubuntu 11.10 "Oneiric Ocelot" Minimal CD 26MB (MD5: 407bf3a2b1d56af8e01aecfc6fdcbc9d, SHA1: 6eebf8cf79ae4f838ef88e43b9caa0ea1a92d2c)
Ubuntu 11.04 "Natty Narwhal" Minimal CD 22MB (MD5: 13507ac70863edd2df11cdd6260011ba, SHA1: 971f67b98323f090f3609f5c7fe78478d564122d)
Ubuntu 10.10 "Maverick Meerkat" Minimal CD 15.6MB (MD5: 3d9f096398991ed1eaa9ff32128e199a, SHA1: ea621a169b55d4c759f19600fea78e4ba7b83ba4)
Ubuntu 10.04 "Lucid Lynx" Minimal CD 14MB* (MD5: d260ca4ad6d0c81bf5cf38a63fa63b5b, SHA1: b4aaf4c8e7c4a11b765a6b37d9e873ecf4f45fc8)
Ubuntu 8.04 "Hardy Heron" Minimal CD 9.8MB* (MD5: d6e7717a9ba527b1d19b677a4243c3e9)

---

### Post by Schr on 2011-10-28
If you want ubuntu without the desktop why not install the server version?

[http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download)

---

### Post by nothingspecial on 2011-10-29
I was suggesting a new install from the minimal cd. If you want to remove ubuntu desktop,

```
sudo apt-get install tasksel
```

Then uncheck ubuntu-desktop.

You can also just turn the gui off.

---

### Post by iamtrying on 2011-10-29
@nothingspecial: The link that you gave. I did as:

Action 1:
1) Make liveUSB
2) New install
3) All failed to get installed

Problem: When you install the Ubuntu from your given link, it cause problems as below:

1) It fails to install GRUB
2) It completes the installation
3) Once you boot there is no more MBR for GRUB menu

4) Whole installation is crashed (see my screen shot plz, black screen)



Please provide a working link?

---

### Post by nothingspecial on 2011-10-29
So you installed the minimal system and you can't boot. I'll have to have a look.

---

### Post by nothingspecial on 2011-10-29
You need to file a bug.

For now, where are you up to?

You have a minimal install with no grub right?

You can fix this by booting from a live cd then chroot and installing grub from there. Do you have a 64bit Ubuntu live cd?

If so you can fix grub using the instructions here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by iamtrying on 2011-10-29
> **Schr said:**
> If you want ubuntu without the desktop why not install the server version?

[http://www.ubuntu.com/download/server/download](http://www.ubuntu.com/download/server/download)

That one does not work either. Because i have to use my boot splash, but server version throws lots of texts.

---

### Post by nothingspecial on 2011-10-29
Grub thread here

[http://ubuntuforums.org/showthread.php?t=1871563](http://ubuntuforums.org/showthread.php?t=1871563)

---

