---
title: "Can't log into Gnome (after unchecking 'Deny TCP connections on Xserver')"
date: 2007-05-23
forum: Desktop Environments
---

### Post by akadruid on 2007-05-23
Hi all,

I logged out of Gnome and now I can't log in - I just get a plain screen the colour I set my background to and nothing else!  Safe mode is the same but with a plain grey box in the top left.  I get this email after entering my user name and password, I don't get the usual splash screen with the icons for nautilus etc that you normally get while it loads.

The last thing I did before I logged out was to follow some instructions I found for trying to set up X forwarding here: [ubuntuforums.org/showthread.php?t=446725]("http://ubuntuforums.org/showthread.php?t=446725&page=2")

   1. On the menu, select System -> Administration -> Login Window
   2. Select the "Security" Tab
   3. Make sure the "Deny TCP connections on Xserver" option is UNCHECKED

I then logged straight out and now I can't log in...  I'm not sure exactly where to look for errors either.

I can still SSH to the box from another, everything seems OK, and I can log in if I pick XFCE from the sessions menu at log in.  but Gnome and Gnome safe mode do nothing.

Can anyone help me?  Thanks in advance!

akaDruid

---

### Post by akadruid on 2007-05-25
If I create another user, I can log into Gnome normally.  Is there some way to reset my Gnome settings on my original user account?

Cheers

akaDruid

---

### Post by akadruid on 2007-06-20
Never mind, I sorted it out by switching to a text console and gradually removing all my .gnome and .gconf files until it let me load gnome.

---

