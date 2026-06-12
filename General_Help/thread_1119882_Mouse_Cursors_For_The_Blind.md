---
title: "Mouse Cursors For The Blind"
date: 2009-04-08
forum: General Help
---

### Post by s1mp13m4n on 2009-04-08
Hello everyone.  I am trying to locate and install mouse cursors that work with my visual impairment.  I have a hard time seeing the default Gnome mouse pointers.  There are plent of options for dexterity issues but not for people with vision problems.  There is nothing in the mouse settings for extra large pointers or mouse trails, etc like you have in Windows XP.  Where can I get mouse cursors that will make Gnome easier to use?  Also how do I install them?  Thank you for the help.

---

### Post by TenPlus1 on 2009-04-08
[www.gnome-look.org](www.gnome-look.org) for all sorts of theming, including mouse pointers...

Note: Ubuntu has a few pointers that can be Resized with the slider in the pointer setup...

---

### Post by wolfen69 on 2009-04-08
```
sudo apt-get install ttf-tiresias
```
will install fonts for the visually impaired.
```
sudo apt-get install big-cursor
```
will install a larger mouse cursor.

using a high contrast theme will also help. it is included in ubuntu.

---

### Post by s1mp13m4n on 2009-04-08
OK I entered the code in a terminal and all installed well.  Now, what do I do with it?  Here is what happened when I entered the commands:

paul@paul-laptop:~$ sudo apt-get install ttf-tiresias
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  psemu-drive-cdrmooby psemu-sound-alsa psemu-sound-oss libfltk1.1
  psemu-input-omnijoy psemu-video-x11
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ttf-tiresias
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 580kB of archives.
After this operation, 1212kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe ttf-tiresias 0.1-1 [580kB]
Fetched 580kB in 2s (227kB/s)        
Selecting previously deselected package ttf-tiresias.
(Reading database ... 138945 files and directories currently installed.)
Unpacking ttf-tiresias (from .../ttf-tiresias_0.1-1_all.deb) ...
Setting up ttf-tiresias (0.1-1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-tiresias
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.

paul@paul-laptop:~$ sudo apt-get install big-cursor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
big-cursor is already the newest version.
The following packages were automatically installed and are no longer required:
  psemu-drive-cdrmooby psemu-sound-alsa psemu-sound-oss libfltk1.1
  psemu-input-omnijoy psemu-video-x11
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I went into System-->Preferences-->Appearence and found that you can custom size your current mouse pointer inside the current theme you are using.  That did help and is usable but I still think it can be better.  I am still open to ideas.  :)

---

### Post by cariboo on 2009-04-08
Have a look at [Orca]("http://live.gnome.org/Orca"), also have a look at System-->Preferences-->Assistive Technologies.

Jim

---

### Post by s1mp13m4n on 2009-04-08
Thanks for the reply.  I have Orca installed but do not really need it.  I have a 22 inch LCD in front of me and I did figure out how to increase the fonts so I am using size 14-16 fonts and the monitor is close to me.  :)  I looked into the assistive technologies section as well and there is nothing there that helps me, it deals more with dexterity issues rather than blindness.  :)

---

### Post by Therion on 2009-04-08
Compiz will enable you to use pointer-trails.  Rather dramatically if you don't mind playing with the configuration sliders.

Juet enable the "Show Mouse" plugin; here's how to configure it:  [http://wiki.compiz-fusion.org/Plugins/Showmouse](http://wiki.compiz-fusion.org/Plugins/Showmouse)

---

### Post by s1mp13m4n on 2009-04-08
Thank you for that link.  I installed CCSM and it is interesting.  I am playing with it but so far it is more of what I am looking for.  It took a bit to figure out why it was not working, then I had to enable desktop effects in Gnome.  I had mine setup with no effects for a clean and fast GUI.  So far this is working very well.  I can use the Negitive feature helps me as well because I can toggle reverse contrast on the fly and use it when needed.  I am working on getting the magnification working but so far I have not got that up and running.  Thank you very much for this help.  This far beyond what Windows can do and sure saves $$$ on the insane price of Zoomtext magnifier for Windows.  I am learning to love Linux more everyday.  I now have another reason not to go back to Windows.

---

