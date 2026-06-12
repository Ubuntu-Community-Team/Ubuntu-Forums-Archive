---
title: "Ubuntu Remaster - Error with Fluxbox / Window Manager"
date: 2006-11-21
forum: Desktop Environments
---

### Post by mikedeatworld on 2006-11-21
Hi all-

This is my first post in a long time on here! Thanks in advance! I'm in a real bind here! I am following a tutorial on how to remaster Ubuntu 6.06, which is located here:

I plan to install serveral tools later, but want to get the hang of things first. 

[https://help.ubuntu.com/community/LiveCDCustomization/6%2e06](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06)

Everything seemed to go very smooth. However, I did receive one error with the command:                                          sudo rm extract-cd/casper/filesystem.squashfs 

I was getting a file not found error, but I moved forward thinking maybe I already deleted the file (it was late last night). 


Through out the tutorial, I was able to remove gnome and install fluxbox 

One notable removal was Gnome. 
apt-get remove gnome* --purge

And I installed fluxbox
apt-get install fluxbox

I was able to build the CD without incident. I boot into my new LIVECD. 

Now when I try to boot/launch fluxbox, I get an error: 

ubuntu@ubuntu:/$ fluxbox
Warning: Failed to open file(/usr/share/fluxbox/nls/en_US/fluxbox.cat)
for translation, using default messages.
Error: Couldn't connect to XServer

When I run startx, I get a grey screen, without any window manager. I can post files, if need, X11, etc.


Just so you know, I am working on this by hand to get to learn Linux and understand the process of making a LivdCD. I am pretty sure, things (I'm not sure where) are pointing to gnome. If you could help me please, figure this out, that would be really awesome! Any help would be awesome!

Any help on resolving this error would be cool:
ubuntu@ubuntu:/$ fluxbox
Warning: Failed to open file(/usr/share/fluxbox/nls/en_US/fluxbox.cat)
for translation, using default messages.
Error: Couldn't connect to XServer



Thanks! 

Mike

---

### Post by mikedeatworld on 2006-11-21
is this the right area for this thread?

---

### Post by mikedeatworld on 2006-11-21
I'm pretty sure, fluxbox is looking for a language pack that I may have removed. I will reinstall this en_US pack it seems to need at the moment. 

If you have any other suggestions, let me know! I'll report what I find out!

Mike D.

---

