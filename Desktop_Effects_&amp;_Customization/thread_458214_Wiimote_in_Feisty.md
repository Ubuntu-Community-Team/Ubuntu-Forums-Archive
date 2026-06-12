---
title: "Wiimote in Feisty"
date: 2007-05-29
forum: Desktop Effects &amp; Customization
---

### Post by RelativelyQuantum on 2007-05-29
Hi all.

I've been reading some interesting things lately about people who have found ways to interface with their Ubuntu using the controller for the Nintendo Wii. I bought one the other day specifically for this, but can't find a simple way to do so. I've tried running the various python scripts which appear in the tutorials from WiiLi.com, but can't seem to get it working. Any feedback or recommendations would be greatly appreciated.

This is a link to a video which sums up what I'm trying to do; its been floating around the forum for a while:

[http://www.youtube.com/watch?v=ALqduQfm09c](http://www.youtube.com/watch?v=ALqduQfm09c)

---

### Post by reclusivemonkey on 2007-05-29
> **RelativelyQuantum said:**
> Hi all.

I've been reading some interesting things lately about people who have found ways to interface with their Ubuntu using the controller for the Nintendo Wii. I bought one the other day specifically for this, but can't find a simple way to do so. I've tried running the various python scripts which appear in the tutorials from WiiLi.com, but can't seem to get it working. Any feedback or recommendations would be greatly appreciated.

This is a link to a video which sums up what I'm trying to do; its been floating around the forum for a while:

[http://www.youtube.com/watch?v=ALqduQfm09c](http://www.youtube.com/watch?v=ALqduQfm09c)

I managed to get this working in Slackware fairly easily, but it doesn't work for me in either Edgy or Feisty, which is a shame as its a great way to control MythTV. Just for reference, this is the tut. I followed;

[http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote](http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote)

---

### Post by simoncm on 2007-06-02
I got this to work in Feisty with the documentation.  There was a little trick with WMD:  an empty file named "__init__.py"(Notice 2 underscores) needed to be in each directory containing the modules for WMD.  This tells python that the subdirectory is an actual subdirectory not a string. 
I placed the WMD directory in my home directory and after making all necessary edits, I executed the wmd.py.  The cursor went flying off to the far corners of the screen.  This will take a little getting used to.  I can see it as a really cool presentation tool.

---

### Post by BlahMan_of.Doom on 2007-06-17
Edit: I'm posting my own thread :S

---

### Post by Eggbanjo on 2007-09-20
took me two days to do, But found using wmgui and wminput, giving the address of the wiimote (using hcitool) worked a treat i.e

wminput 00:19:FD:DB:33:C9

this means i can use it as a mouse - bloody great for moving around beryl with, just looking for more appz to use it on!

---

### Post by salatmensch on 2007-09-25
how did you get wmgui and cwiid compiled? 
i fail at "libc6" not found and "gtk+2.0" not found although both are installed...

---

