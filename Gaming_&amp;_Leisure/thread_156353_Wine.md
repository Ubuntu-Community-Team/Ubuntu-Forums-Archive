---
title: "Wine"
date: 2006-04-06
forum: Gaming &amp; Leisure
---

### Post by Fatstink on 2006-04-06
I am having issues downloading wine.  I am using an amd 64 X2.  does anyone know of a way I can install wine???

---

### Post by Sutekh on 2006-04-06
- Having an AMD X2 won't have an effect.  Are you using the 32bit version of Ubuntu? Or the 64bit?

 - Here's how to get wine

 - Open a terminal window (from the Menu; Applications -> Accesories -> Terminal), and issue the commands
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
sudo nano /etc/apt/sources.list
``` - This will backup your apt-get repository sources list, so you can always change it back, and then allow you to edit the list.

- To install wine you will need the wine repository; add these lines to your sources.list
```

deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/
``` - Then save the file (Ctrl+O) and exit (Ctrl+X).

 - Update the repositories using
```
sudo apt-get update
```

 - Finally you can install wine using
```
sudo apt-get install wine
```

 - Once wine is installed youshould run **winecfg** to setup options such as sound, extra drives, etc.
```
winecfg
```

 - To install a game use wine in the following manner
```
wine /path/of/program.exe
```

 - For example running the setup.exe program on a CD-ROM
```
wine /media/cdrom0/setup.exe
```



 - If you are using the 64bit version of Ubuntu, when you come to installing it, you should try this

[Wine for   64bit Ubuntu](http://ubuntuforums.org/showpost.php?p=537708&postcount=5)

---

### Post by Fatstink on 2006-04-06
I am using 64-bit Kubuntu 5.10 Breezy Badger.  When I add those lines and run apt-get update I get this.
--------------------------------------------------------------------------------------------------------------
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Get:2 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release [110B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:5 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release [112B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Get:6 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages [1099B]
Get:7 [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources [580B]
Fetched 2280B in 2s (775B/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
--------------------------------------------------------------------------------------------------------------------------
then I run apt-get install wine and I get
*************************************************************************
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
**************************************************************************

It seems to miss the wine package in the update.

---

### Post by Sutekh on 2006-04-06
Ok, and you are using the 64bit Breezy too.

So download the .deb package

[http://wine.sourceforge.net/apt/breezy/wine_0.9.11~winehq1-1_i386.deb](http://wine.sourceforge.net/apt/breezy/wine_0.9.11~winehq1-1_i386.deb)

And install it using the instructions in the post I linked.  There might be some issues that you encounter, but the forum is rife with Wine/64bit threads, I'm sure you could get it working.

---

### Post by Fatstink on 2006-04-06
Okay I get an unpacking error but I got all the files via CVS earlier I just don't know now what to do with them.  do you have any idea?

---

### Post by Sutekh on 2006-04-06
Sorry I have no idea what to with CVS files.

Have you checked out

[Wine HQ - The Wine CVS Tree](http://www.winehq.org/site/cvs)

---

### Post by Fatstink on 2006-04-06
Yeah, I downloaded all files and there are in a directory called wine and I have no idea what to do with them.

---

### Post by Sutekh on 2006-04-06
Ok then, well getting back to the .deb package.  Did you install it by downloading that .deb and then using
```
sudo apt-get install ia32-libs*
sudo dpkg -i --force-architecture wine_0.9.11~winehq1-1_i386.deb
```
Can you post the output and error (if any) from those commands?

---

### Post by Fatstink on 2006-04-06
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 65557 files and directories currently installed.)
Unpacking wine (from wine_0.9.11~winehq1-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.11~winehq1-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/wine/gdi32.dll.so')
Errors were encountered while processing:
 wine_0.9.11~winehq1-1_i386.deb

---

### Post by Sutekh on 2006-04-06
Okay that error sucks, I can't find anything really helpful regarding it

The only thing I could suggest is to re-download the file using wget (appraently it good for maintaining the file's integrity)
```
wget http://wine.sourceforge.net/apt/breezy/wine_0.9.11~winehq1-1_i386.deb
```

If that doesn't work, and Wine is really important, you could consider setting up a chroot environment (this allows you to run 32bit programs -> wine in the 64bit architecture) or think about using the 32bit version of Ubuntu.

---

