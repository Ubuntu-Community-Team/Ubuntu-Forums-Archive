---
title: "Need libartskde.so.1. What to do?"
date: 2009-06-09
forum: General Help
---

### Post by ram2500 on 2009-06-09
I need libartskde.so.1 for a program. How do I get it? I am using Jaunty (9.04) and it doesn't have it (obviously). Can someone point me to it?

---

### Post by kevdog on 2009-06-09
What does it say when you type

sudo apt-cache search libartskde.so

---

### Post by ram2500 on 2009-06-12
It says nothing, However, I did install noatun but when I click it from the menu, it doesn't do anything. When I type "noatun" in the terminal, it doesn't open, instead, it says this: 

**noatun: error while loading shared libraries: libartskde.so.1: cannot open shared object file: No such file or directory**

I know I need libartskde.so.1 - but I don't have it! I cannot get it. How on *Earth* do I get it???

---

### Post by ram2500 on 2009-06-12
I give up. I am backing up all of my files and going back to 8.10. New is certainly not always the best...but, I don't benefit from the ext4 filesystem. Oh, well. 

WHY do the maintainers remove repositories that people might need?
Ugggggghhhhh....(*,)

---

### Post by gradinaruvasile on 2009-06-12
sudo apt-get install libart2 
?

---

### Post by ram2500 on 2009-06-12
I've already started to do the backup/uninstall to get to 8.04 where it will work, but I will certainly try this after this is done to see if it works on a spare machine. Stupid me...never taking my time. 

I hope this works...I reallywant the ext4 filesystem and all that good stuff.:p

---

### Post by ram2500 on 2009-06-12
OK, I reinstalled 9.04 and installed libart2. I installed Noatun, the program that needs libartskde.so.1, will not start up. The terminal says: 

**noatun: error while loading shared libraries: libartskde.so.1: cannot open shared object file: No such file or directory**

I am very F-R-U-S-T-R-A-T-E-D over something that should be very straightforward and simple. Why was libartskde.so.1 done away with in 9.04?
Are there alternatives to getting this to work? Where can I get libartskde.so.1, so that I can use Noatun? Or, if I have it already, how do I enable it?

I need to take a deep breath. I'm getting red in the face:)

I have heard that I am not the only one with this libartskde.so.1 problem; where or who can I tell so that this is fixed?

---

### Post by mc4man on 2009-06-12
I don't believe you'll find it in there (libart2 ), it would have been included in kdelibs4c2a. 

Files included in kdelibs4c2a (from my hardy
> ...........clipped
/usr/bin/filesharelist
/usr/bin/kfmexec
[COLOR="Blue"]/usr/lib/libartskde.so.1[/COLOR]
/usr/lib/libDCOP.so.4
/usr/lib/libkabc_dir.so.1
........clipped

It may be possible to compile it back in, don't have jaunty so can't say, maybe I'll boot up a live cd later and see

or it may be possible to compile it out of your app

Edit: did you run sudo ldconfig after your attempt to insert the .so as in other post?, though there is no aRts in jaunty so may be a moot point anyway

---

### Post by mc4man on 2009-06-12
well you can install noatun on jaunty, whether it plays much of anything I don't know. (plays a .wav, won't play a .mp3 yet.

Didn't know where you got it from so used the hardy updates version, though may be a better way.

Screen shows it playing and packages needed to install from this method (installed from top to bottom, left row to right. (though could do a dpkg -i *.deb after assembling them all.

Where are you getting noatun from?

Also now plays an ogg, maybe there are some plugins?

Edit
While you can add support for other formats, hardly seems worth the effort and any potential unknown issues

---

### Post by IEKnight on 2009-07-10
Hope this Helps - Worked for me.

Goto [http://packages.debian.org/lenny/kdelibs4c2a]("http://packages.debian.org/lenny/kdelibs4c2a").

Scroll down to the download section, and check the list of files for your platform (search for libarts using your browser)

You should find the following lines:
/usr/lib/libartskde.so.1
/usr/lib/libartskde.so.1.2.0

so now, download the package, but save it, don't try to run or you will get a 'later version already installed message'.

deb files are just a special form of archive.
Open it with archive manager.
There are 2 sub-archives. Open data.tar.gz.
Navigate to /./usr/lib in the archive.
Find libartskde.so.1 & libartskde.so.1.2.0.
Extract them.

Now open a terminal, and type *gksu nautilus* (if you use gnome), otherwise *gksu dolphin* (if KDE 4), etc.

navigate with nautilus/dophin/etc. to where you extracted the files, and copy them to /usr/lib.

Hopefully it will all work now ;)

---

