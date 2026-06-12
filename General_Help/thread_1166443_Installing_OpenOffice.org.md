---
title: "Installing OpenOffice.org?"
date: 2009-05-21
forum: General Help
---

### Post by pentium_3 on 2009-05-21
Hi again ):P

I installed Xubuntu on my brother's old computer a few months ago. So far, it has been very good overall, with some hiccups. Shortly after I installed Xubuntu, I also installed OpenOffice.org version 2.4 as the main office suite. 

Unfortunately, there are a number of files he needs in the new OOXML format (.docx, .pptx, etc.) that OpenOffice cannot read. Many of these are very important, and I'm sick of letting my brother use my Windows machines to gain access to OOXML files he gets from school. I've heard that OpenOffice.org version 3 has the ability to read these. I went to download it, but all I am confronted with is a mind-boggling package. OpenOffice's site tells me to go through a bunch of command line BS to get this installed. Is there a completely graphical method to install the new program over the old one? Any way to avoid the terminal would be great.

---

### Post by BslBryan on 2009-05-21
Hello, pentium_3. :-)

I'm sorry, but as of now, there is no graphical way to do this.  However, in the OOo package, there are installation instructions, as well as hundreds of tutorials on the internet.  The terminal isn't quite as scary as you might think. :p

I can point you to a tutorial if you need one.  Best to you, and your brother, and good luck!

---

### Post by AlexDudko on 2009-05-21
Why don't you just upgrade to current distribution Jaunty? You'll have then OOO-3.0.1 by default.
Abiword-2.6.6, which is included in Xubuntu-8.10 should also read these files.

---

### Post by jonathonblake on 2009-05-21
> **pentium_3 said:**
> 
Unfortunately, there are a number of files he needs in the new OOXML format (.docx, .pptx, etc.) that OpenOffice cannot read. 

Oxygen Office 2.4 can read those file formats.

> machines to gain access to OOXML files he gets from school

Have your brother ask the school when they intend to provide documents in a file format that meets ISO specifications. 

ISO/IEC 26300:2006 is the only office document format with an ISO specification that has vendors currently shipping implementations of it.

No vendor has announced support for, much less is shipping a product that meets ISO/IEC 29500:2008 specifications. (Microsoft announced that they would not support those specifications until 2012 at the earliest.)

>  Is there a completely graphical method to install the new program over the old one? Any way to avoid the terminal would be great.

Installing OxygenOffice in a WINE bottle would avoid the terminal.

There should be a shell script in the download from OOo that is named "upgrade".   If so, run that, and everything should be correctly installed. (Should be, because there are a number of differences between OOo as delivered by Sun, and OOo as delivered by Ubuntu. Some of those differneces don't play well together, when upgrading from one version, by one vendor, to a new version by a different vendor.)

jonathon

---

### Post by Aearenda on 2009-05-21
There is a way to upgrade graphically, using a private package archive (PPA) maintained by the Ubuntu OO developers. However, it is currently in transition from OpenOffice 3.01 to 3.1, and I recommend waiting until the build is complete before upgrading, otherwise help files (at least) will be missing.

The build status is shown at [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
Wait until all the packages have a green tick alongside for your version.

For upgrade instructions see [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by pentium_3 on 2009-05-22
> **AlexDudko said:**
> Why don't you just upgrade to current distribution Jaunty? You'll have then OOO-3.0.1 by default.
Abiword-2.6.6, which is included in Xubuntu-8.10 should also read these files.

This computer is extremely old... like 650 MHz Pentium III with about 224 MB of RAM. I doubt it could handle any newer release. For anyone who suggests we get a new computer, rest assured he will be getting a new one after summer... but for now, this is what we got.

> **BslBryan said:**
> Hello, pentium_3. :-)

I'm sorry, but as of now, there is no graphical way to do this.  However, in the OOo package, there are installation instructions, as well as hundreds of tutorials on the internet.  The terminal isn't quite as scary as you might think. :p

I can point you to a tutorial if you need one.  Best to you, and your brother, and good luck!

It seems like the general consensus is that the Terminal is the only way to upgrade this without using some sort of third-party tool (which, on Linux, I would prefer to avoid). If you could point me to the tutorial, that would be great. 

PS are the instructions the same for Xubuntu as they are for Ubuntu? If you could let me know that would be great :D

---

### Post by scouser73 on 2009-05-23
Here's my tutorial for installing the latest version of OpenOffice.

Firstly, go to the OpenOffice website: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and download the Linux .deb file.

Once you have done that, extract the .deb file, **OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz** then you'll see a file called **OOO310_m11_native_packed-4_en-US.9399**

You can remove the existing version of OpenOffice if you wish with this command: **sudo apt-get remove openoffice*.***

Copy and paste **OOO310_m11_native_packed-4_en-US.9399** onto the desktop then open Terminal and paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

Then paste this command: **sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9393_all.deb**

Once you've done that you'll find OpenOffice 3.1.0 in Office.

---

### Post by pentium_3 on 2009-05-23
Thanks for all the help, specifically in the command line sector. But... when I input this command line:

**alexander@Xubucomp:~$ sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb**

It keeps giving me this:

[B]dpkg: error processing /home/alexander/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/alexander/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb[/B]

I would really, really like to get this installed. What exactly is the problem here?

---

### Post by pentium_3 on 2009-05-23
Actually, please disregard the previous post. I accidentally downloaded the wrong package. OpenOffice.org 3.1 was installed successfully (after removing OpenOffice.org 2.4) and we are now able to read the new OOXML files. Thanks everyone!

(no doubt I'll be back here soon though...)

---

