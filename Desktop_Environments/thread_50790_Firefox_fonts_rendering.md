---
title: "Firefox fonts rendering"
date: 2005-07-21
forum: Desktop Environments
---

### Post by genbie on 2005-07-21
Hi,

I am having a problem with firefox rendering where every third/half page or so, a line is not rendered clearly. I have to highlight the line for it to be rendered in full. I mean the fonts are like half rendered. I installed epiphany and the same problem exists. I do not experience the problem in other applications and I did not have it in firefox before so it maybe something to do with upgrading to the latest mozilla-firefox? I re-installed all mozilla packages but the problem is still there!

I was wondering if someone had experienced the same problem or could help please?

Thanks.

---

### Post by oobuntoo on 2005-07-22
I used to have this problem. I don't think this is a fault of Firefox, but how you configured your xorg.conf file. Take a look at Section "Monitor" of xorg.conf to see if you have "DisplaySize" option specified. If you don't have it, add it. If you do have it, make sure it has the corect values that correspond to the display resolution you use for your desktop. You need to become root or super user to edit xorg.conf, whic is located under /etc/X11. Here is how you determine the correct values:

	DisplaySize	270	203	if display resolution is 1024x768
	DisplaySize	338	254	if display resolution is 1280x960
	DisplaySize	338	270	if display resolution is 1280x1024
        DisplaySize	370	277	if display resolution is 1400x1050
	DisplaySize	423	370	if display resolution is 1600x1400

if you have different resolution from above list, use this formula

(pixelsize/96)*25.4

For example: if you have your desktop display set to 1600X1200
then you have (1600/96)*25.4=423 and (1200/96)*25.4=317
so your DisplaySize in your xorg.conf would be 

DisplaySize	423	317

You need to restart X (Ctrl+Alt+Backspace) or reboot for changes to take effect.
This may or may not help you, but it solved my firefox rendering problem. You may wan to read this [thread](http://ubuntuforums.org/showthread.php?t=20976&highlight=DisplaySize)  too.

---

### Post by genbie on 2005-07-30
Thanks a lot for your help oobuntoo. My fonts are working great now  :)

---

