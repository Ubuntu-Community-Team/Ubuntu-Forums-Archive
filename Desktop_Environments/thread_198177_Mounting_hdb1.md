---
title: "Mounting hdb1"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Guns90 on 2006-06-16
I just did an install of Dapper on hda1 and moved my old hda1 (Breezy) to hdb1.  Both are showing up in the 'computer-file browser', but I cannot mount hdb1.  I get error codes...

error: device /dev/hdb1 is not removable

error: could not execute pmount 

I want to transfer all the data files from hdb1 to hda1.  

????

---

### Post by scxtt on 2006-06-16
what command are you executing and what's your /etc/fstab look like?

---

### Post by Guns90 on 2006-06-16
I have simply tried to mount it using the GUI;  computer>227.4 GB Volume then I double clicked on it.

And sorry, but I'm too new to this to tell you what my /etc/fstab looks like

---

### Post by aysiu on 2006-06-16
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by Guns90 on 2006-06-16
That did the trick aysiu.  Thanks.    Let me ask you something else, please.  Is it possible to bring all the settings I have in Breezy (hdb1) over to Dapper (hda1)?

---

### Post by aysiu on 2006-06-16
Yes, but it's tricky.

Essentially, you have to copy the hidden folders from one /home/gun directory to the other.

I would recommend doing this one at a time. That way, you can see if any don't copy over correctly.

For example, if you have a .gnome on Breezy and a .gnome on Dapper, I'd rename the Dapper .gnome to be .gnome.old before copying over the Breezy .gnome.

If you're feeling adventurous and want to keep both Breezy and Dapper on the same settings all the time, consider setting up a separate /home partition that both can share:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by scxtt on 2006-06-17
couldn't you tar up your /home in breezy and untar it in dapper? ... i'm not sure if there's a flag for copying "hidden" folders, but you should be able to do something like that ...

---

