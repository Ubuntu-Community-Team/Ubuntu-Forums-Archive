---
title: "Installer won't use the downloaded image"
date: 2009-01-02
forum: General Help
---

### Post by nachomania on 2009-01-02
I'm trying to get wubi to install on an AMD 64bit vista laptop. I downloaded a 32 bit image (Desktop, i386), and Wubi-8.10-rev515 from sourceforge, then put them in the same folder. If I try to run the installer, it first off takes a long time with the checksums, then tries to download another image (Or, if the wireless is off, asks me to reconnect to the internet). Any ideas?

EDIT
-I dragged the .iso onto the wubi installer, it worked!

---

### Post by nachomania on 2009-01-02
Ok, in the install folder, MD5SUMS-metalink.asc says jaunty amd64. I've downloaded a 8.04 image and wubi installer. the installer fails at renaming somthing. There is nothing to read on this. Why isn't it using the damn image? Do I need a .md5 thing or something? Please help!

---

### Post by creek23 on 2009-01-02
> **nachomania said:**
> Do I need a .md5 thing or something?

You need to MD5 hash to make sure you downloaded the image correctly.

---

### Post by brandon88tube on 2009-01-02
> **nachomania said:**
> Ok, in the install folder, MD5SUMS-metalink.asc says jaunty amd64. I've downloaded a 8.04 image and wubi installer. the installer fails at renaming somthing. There is nothing to read on this. Why isn't it using the damn image? Do I need a .md5 thing or something? Please help!

I'm not sure what you mean by it saying Jaunty, but that sounds like it is the new version of Ubuntu that is in development right now. Are you sure you have the correct ISO?

---

### Post by nachomania on 2009-01-03
In the install folder, the file named ``MD5-metalink`` has the following written in it. Why would it say jaunty... 

656cc3542823bfa65b5123a7845f84a8  jaunty-desktop-amd64.metalink
0f702a13be03d8f9d9e8b7da28860d8e  jaunty-desktop-i386.metalink

The error message, which is just blank, happens at ``Rename: C:\ubuntu\install\MD5SUMS-metalink.gpg ->C:\ubuntu\install\MD5SUMS-metalink.asc``

If I put the Wubi installer in the same folder (Just a folder on the Desktop, by the way), it still asks me (If I turn the connection off) to connect to the internet. Can`t it use the image I downloaded

The md5 is c69e34e92d5402d1b87e6babc739f774, which is right for hardy desktop i386

---

### Post by creek23 on 2009-01-03
> **nachomania said:**
> 656cc3542823bfa65b5123a7845f84a8  jaunty-desktop-amd64.metalink
0f702a13be03d8f9d9e8b7da28860d8e  jaunty-desktop-i386.metalink

...

The md5 is c69e34e92d5402d1b87e6babc739f774, which is right for hardy desktop i386

But not for jaunty, which is the ISO you are installing. This probably means that the ISO you downloaded/burned is corrupted in some parts.

c69e34e92d5402d1b87e6babc739f774 did not match any of the jaunty MD5 hashes.

---

### Post by nachomania on 2009-01-03
Ok, I kind of mudded things up there. First, I attempted to install off a Hardy Heron CD (The menu. I used to CD before, worked on a full install). It attempted to connect to the internet. So I tried burning an Intrepid CD, and tried it, same thing. Then, seeing as how those two didn't work, I downloaded the wubi installers for either version, put them in the desktop (with the iso's, which I had downloaded again from different sources), and tried them. They quit with some blank error, while renaming the file I mentioned above. I tried Hardy and Intrepid, not Jaunty. WinMD5SUM confirmed the hardy iso. Every time, I go to C and uninstall the ubuntu folder there through the uninstaller. Can't the installer work without an internet connection?

---

### Post by brandon88tube on 2009-01-04
I want to make sure you have the correct files so I would like you to follow these instructions and download these files. You may have already done these exact steps, but I am trying to make sure you did it correctly.

Go here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), select Ubuntu 8.10 Desktop (the latest version): Includes the latest enhancements and is maintained until 2010, the location closet to you, then select 32-bit or 64-bit on the bottom. I take it you want 32-bit. Now download this version of wubi.exe here [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php)

Once those are downloaded, throw the 2 files in a folder together. Disconnect your internet connection and then run the wubi.exe

---

