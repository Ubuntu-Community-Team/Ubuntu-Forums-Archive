---
title: "Cant find download directory for terminal install of app"
date: 2009-03-15
forum: General Help
---

### Post by JerryI on 2009-03-15
I have just reformatted my dual-boot XP/Hardy system to give me more room for Ubuntu and I tried to look at a Youtube tutorial and needed adobe flashplayer which I downloaded, but now I can't find the tar.gz file to install it because it isn't on the desktop like it was in my old system.  How do I find an install with the gui and/or with terminal?

---

### Post by ju2wheels on 2009-03-15
Open Firefox, select Edit-> Preferences in the menu and select Main tab. In the middle theres a Downloads section that shows where things go by default when downloaded.

Are you running 32bit or 64bit?

---

### Post by JerryI on 2009-03-15
Default is to desktop, but the file doesn't appear there.  Anyway, now I have a bigger problem. I had a tar.gz file on my desktop for VMware, so I did a tar op on it and it created a vmware-distrib folder on my desktop with a zillion files in it.  So, like instructions said, I went to the directory with all the files and issued the command ./configure and got bashed by No such file or directory.  I don't think I'll ever get the hang of this system.

---

### Post by ju2wheels on 2009-03-15
You are just grabbing the wrong thing thats all. Installers for Ubuntu end in .deb. What your are downloading is the source code which is not what you want. I recommend you first learn how to use the software installer built into Ubuntu.

Have a read through some of the sections here first: [https://help.ubuntu.com/8.04/index.html](https://help.ubuntu.com/8.04/index.html)

---

### Post by mb_webguy on 2009-03-15
> **JerryI said:**
> Default is to desktop, but the file doesn't appear there.  Anyway, now I have a bigger problem. I had a tar.gz file on my desktop for VMware, so I did a tar op on it and it created a vmware-distrib folder on my desktop with a zillion files in it.  So, like instructions said, I went to the directory with all the files and issued the command ./configure and got bashed by No such file or directory.  I don't think I'll ever get the hang of this system.

If you haven't cleared your download history, you can right-click on the download and select Open to open the download using the default application.  For a tarball, this would be Archive Manager (actually File Roller).  Then you can extract it to any location you want.

As to your other issue, the ./configure command has to be run from the directory where you extracted the tarball.  The "." preceding the slash means "this directory", so ./configure means "run the configure script located in the current directory".  So you need to use the cd command to change to the proper directory before issuing this command.

Also, a tarball (i.e. tar.gz, tar.bz, .tgz, etc.) is basically the same thing as a zip file.  Yes, these archives are commonly used for distributing source code for Linux applications, but they can contain anything.  Make sure a file called "configure" actually exists in the extracted archive before you try running it.  It's possible that software distributed in a tarball could use an "install.sh" script or other means of installing the software.

And, of course, as ju2wheels said, it's much better to install software from the repositories (using Add/Remove Applications, Synaptic Package Manager, or apt-get in the terminal) or using a deb package than by compiling from source.

---

### Post by sgosnell on 2009-03-15
When you go to the Adobe website, select .deb for Ubuntu as the type file you want, then when Firefox asks, tell it to open the file with gdebi.  The install will be automatic.

---

