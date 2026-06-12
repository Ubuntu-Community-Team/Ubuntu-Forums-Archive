---
title: "Possible to start Unison sync when an USB stick is connected ?"
date: 2005-08-19
forum: Desktop Environments
---

### Post by AndreasMeier on 2005-08-19
Hi there,

I'm wondering how it is possible to start an Unison sync,
when an USB stick gets mounted ?

I've Kubuntu 5.04 running on my desktop and when I connect my USB storage device, the icon appears on the desktop.
When you click on it, the USB stick gets mounted into your filesystem.
All works pretty well.
In addition I have an unison script, which synchronizes all files on the stick with a location on my desktop.

So, how is it possible to automate the last step and start the unison script when the stick gets mounted ?

Any ideas ?

Regards
Andreas

---

### Post by jasmuz on 2005-08-20
Check out these threads to see if they can be of use: 

[http://www.ubuntuforums.org/showthread.php?t=26534](http://www.ubuntuforums.org/showthread.php?t=26534)

[http://www.zombix.org/?page_id=68](http://www.zombix.org/?page_id=68)

---

### Post by AndreasMeier on 2005-08-20
Thanks for the links.
But the problem is not, which tool to take or which config to make,
its just how to start an unison command (or maybe any other command as well), when the usb stick gets mounted.

Regards
Andreas

---

### Post by diegoma on 2008-02-05
Three years later comes the answer :-)

Create a file in your USB stick top folder named autorun. Then it will run automatically when you plug the USB stick.

You may need to enable autorun in your machine. Open the dialogue in System - Preferences - Removable Drives and Media, select the Storage tab, and select the checkbox "Auto-run programs in new devices and media"

Now my question is, how to do the same when unmounting the USB stick?

Diego

---

### Post by paxmark1 on 2008-03-01
side issue.

I had problems with unison between puter and USB, but got it to work in the text mode via appending 

 -perms=0


How can I get that set up for the graphical GTK version of unison?

peace

---

### Post by BennBuntu on 2008-05-10
> **paxmark1 said:**
> side issue.

I had problems with unison between puter and USB, but got it to work in the text mode via appending 

 -perms=0


How can I get that set up for the graphical GTK version of unison?

peace

unison-gtk uses *.prf files located in your home folder.
 ~/.unison 
One for each sync you've setup. for my fat32 usb disk I've added

owner = false
perms = 0

---

