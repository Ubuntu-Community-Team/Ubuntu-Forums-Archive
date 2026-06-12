---
title: "Prolem in compiling GIMP 2.4.3"
date: 2007-12-25
forum: Desktop Environments
---

### Post by Baloon on 2007-12-25
Hello

I am using Ubuntu 7.1 The default gimp version comes with this release is 2.4.0.rc3 and there was some problem with that version. I was trying to install the latest one available in gimp site - that is 2.4.3. I am having difficulties in following.

1. How do I update the existing package to the latest available. How do I configure in my package configuration section for getting this done in Ubuntu

2. I thought of installing from source. So downloaded the tar ball from GIMP site and tried to compile that. I got the following error.

---START
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.12.3... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: Test for GLIB failed. See the file 'INSTALL' for help.
--END

So I think I need to upgrade my GLIB also- But not sure how to check the existing version of GLIB. How do I know the installed package version using apt tools.

3. After getting this information, I need to upgrade GLIB ( if required ) then how do I resolve all the dependancies ?

so basically what is the best way to upgrade GIMP package in Ubuntu :-)

Thanks
Baloon

---

### Post by markharding557 on 2007-12-29
not sure if this is what you want,you can get gimp 2.4.2 in deb package here
[http://www.getdeb.net/]("http://www.getdeb.net/")

---

### Post by hhhhhx on 2007-12-30
cant you just get it from the reposatorys

---

### Post by markharding557 on 2007-12-31
gimp 2.4.2 is in hardy repository and has not been backpoted yet
gimp 2.4.3 is not in the repositorys at all

---

### Post by LinuxFriend on 2007-12-31
I ran into similar issues while trying to install this version of Gimp from source. What I did to get things to install was to read the install file first to look for libraries that I might not have installed (especially the 'dev' packages of those libraries - see below). 

Open the config.log that is generated each time you run the ./configure command to see a full log of the configuration process that may help point to problems.

The issues I ran against was that the 'dev' packages for several libraries were not installed on my computer. I wound up running Synaptic Package Manager (SPM from now on) and search for each library that config was complaining about.

Once you get all the dependencies satisfied so that it compiles, you will see a list of things that were not installed and why they didn't install (namely, what libraries were not found). Use the steps above to install these missing libraries and then run configure again until you have all the libraries taken care of.

Note that the installation notes tell you to uninstall the existing version of Gimp before installing the new version or there may be problems. I tried to uninstall the old Gimp, but in the list of apps that SPM was going to uninstall included many things I didn't want to uninstall such as ubuntu-desktop!

To work around this, changed my menu item for Gimp to point to the new Gimp in the directory where I installed it (otherwise, you will get an error about incompatible libgimp library versions). I use KDE mostly, so my menu item was calling 'gimp-2.4 %U' (which caused the issue above). I changed the 'command' to: 
[home directory]/[gimp installation directory]/gimp-2.4.3/app/gimp-2.4

Once this was set, I could run 2.4.3 without issues. Likewise, I could cd to the directory mentioned above and type 'gimp-2.4' and it would work also. 

Now I am off to see how to install the latest version of the help ...

---

### Post by TeaSwigger on 2007-12-31
Unfortunately I could use the file support added subsequent to the default version in Gutsy. Running

```
sudo apt-get build-dep gimp
```

may tell you what's needed and may install required packages for you. In my case - running Kubuntu Gutsy - that would be some 44 packages with libs, devs, keyrings, bonobos and Gnomes galore oh my! Whether those versions will build 2.4.3, that's the question, but with me using Kubuntu and needing to add 44 packages, I'll try the getdeb version first.

---

### Post by LinuxFriend on 2008-01-02
I did manage to get Gimp 2.4.3 running from source and did get the latest documentation installed (there was documentation that was newer than what came with 2.4.3).

I use UFRaw raw image conversion tool to convert my Nikon raw image files (NEF files). I decided to install the latest version of this too from a package I found outside of the Ubuntu repositories. UFRaw worked well as a stand alone tool, but the Gimp plug-in did not install in my updated Gimp installation and the stand alone version of UFRaw would not send images to the Gimp (Gimp would load and then complain that it couldn't open the image). 

I wound up installing UFRaw from source and all was well in the world. The plug-in installed into the new Gimp and the stand-alone version of UFRaw still worked fine (and had no problem of sending images to the Gimp from within the stand alone interface).

I am not sure if you may run into issues with other external plug-ins if you install Gimp from source, but if you do, try installing the plug-in from source also.

---

### Post by zeroconf on 2008-01-11
I found the tutorial [http://www.davehayes.org/2007/11/01/howto-install-the-gimp-241-on-ubuntu-710-gutsy](http://www.davehayes.org/2007/11/01/howto-install-the-gimp-241-on-ubuntu-710-gutsy) and tried it with Gimp 2.4.3 but it said:
```
$ uupdate -u ../gimp-2.4.3.tar.bz2
uupdate: a native Debian package cannot take upstream updates
```

Also there is no Autopackage version of Gimp 2.4.x series - [http://autopackage.org/packages/](http://autopackage.org/packages/)

Also tried [http://packages.debian.org/sid/i386/gimp/download](http://packages.debian.org/sid/i386/gimp/download) and cannot install them due to unsatisfied dependencies and also sudo apt-get install -f did not help :(

I'm stuck :(

---

### Post by TeaSwigger on 2008-01-11
> **zeroconf said:**
> I found the tutorial [http://www.davehayes.org/2007/11/01/howto-install-the-gimp-241-on-ubuntu-710-gutsy](http://www.davehayes.org/2007/11/01/howto-install-the-gimp-241-on-ubuntu-710-gutsy) and tried it with Gimp 2.4.3 but it said:
```
$ uupdate -u ../gimp-2.4.3.tar.bz2
uupdate: a native Debian package cannot take upstream updates
```

Also there is no Autopackage version of Gimp 2.4.x series - [http://autopackage.org/packages/](http://autopackage.org/packages/)

Also tried [http://packages.debian.org/sid/i386/gimp/download](http://packages.debian.org/sid/i386/gimp/download) and cannot install them due to unsatisfied dependencies and also sudo apt-get install -f did not help :(

I'm stuck :(

I'm no expert but it doesn't look to me like that'd work with 2.4.3 in ubuntu... 

Have you compiled apps from source before? 

Have you tried my suggestion? Make sure you have the source repositories enabled (check repositories in Synaptic). Run my suggestion, sudo apt-get build-dep gimp. Extract gimp-2.4.3.tar.bz2. Open terminal in the resulting folder, gimp-2.4.3. Try running ./configure and see what you get... 

If not perhaps try the .debs available at [http://www.getdeb.net/app.php?name=Gimp](http://www.getdeb.net/app.php?name=Gimp) ? If they'll do, that'd be a whole lot easier.

---

### Post by zeroconf on 2008-01-13
> **TeaSwigger said:**
> I'm no expert but it doesn't look to me like that'd work with 2.4.3 in ubuntu... 

Have you compiled apps from source before? 

I made as tutorial said. Yes, I'm compiled apps before.

> **TeaSwigger said:**
> 
Have you tried my suggestion? Make sure you have the source repositories enabled (check repositories in Synaptic). Run my suggestion, sudo apt-get build-dep gimp. Extract gimp-2.4.3.tar.bz2. Open terminal in the resulting folder, gimp-2.4.3. Try running ./configure and see what you get... 

If not perhaps try the .debs available at [http://www.getdeb.net/app.php?name=Gimp](http://www.getdeb.net/app.php?name=Gimp) ? If they'll do, that'd be a whole lot easier.

Actually that tutorial ([http://www.davehayes.org/2007/11/01/howto-install-the-gimp-241-on-ubuntu-710-gutsy](http://www.davehayes.org/2007/11/01/howto-install-the-gimp-241-on-ubuntu-710-gutsy)) said to run sudo apt-get build-dep gimp.

But currently is 2.4.2 available:
```
$ sudo apt-cache policy gimp
gimp:
  Installed: 2.4.2-0ubuntu0.7.10.1
  Candidate: 2.4.2-0ubuntu0.7.10.1
  Version table:
 *** 2.4.2-0ubuntu0.7.10.1 0
        500 http://ee.archive.ubuntu.com gutsy-updates/main Packages
        100 /var/lib/dpkg/status
     2.4.0~rc3-1ubuntu7 0
        500 http://ee.archive.ubuntu.com gutsy/main Packages
```

Even there is 2.4.4. already available ([http://developer.gimp.org/NEWS-2.4](http://developer.gimp.org/NEWS-2.4)) is that 2.4.2 much better than 2.4.0 RC3.

I also installed the package language-selector and using that, I installed (it automatically offered) also my local language (Estonian) support under Kubuntu for Gtk-based apps like Gimp also is. Thanks for reply! So, currently there is everything OK.

---

