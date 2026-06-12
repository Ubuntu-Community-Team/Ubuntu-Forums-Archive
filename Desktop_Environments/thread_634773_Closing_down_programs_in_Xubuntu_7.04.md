---
title: "Closing down programs in Xubuntu 7.04"
date: 2007-12-08
forum: Desktop Environments
---

### Post by getmeoutofhere on 2007-12-08
When I close down Xubuntu I expect all my programs to be closed down.  Yet when I start up the windows for the programs I was using in the previous session are still there.  Even if I make it clear that I don't want the session saved, by unchecking the appropriate box.  Any ideas?  

BTW I can't get Xubuntu 7.10 to work properly.

---

### Post by getmeoutofhere on 2007-12-08
Still getting nowhere, though this thread seemed to hint at an answer:

[http://ubuntuforums.org/showthread.php?t=264011&page=2](http://ubuntuforums.org/showthread.php?t=264011&page=2)

In particular this:

[COLOR="Red"]September 24th, 2006
kblood's Avatar 	
kblood kblood is offline
Just Give Me the Beans!
	  	
Join Date: Jun 2005
Beans: 52
Re: Switched from Ubuntu to Xubuntu: apps keep auto-starting
Ok, found it and solved it.

It was the .desktop files in .config/autostart/
They have a setting: X-GNOME-Autostart-enabled=(true or false)
It seems that XFCE, regardless of that setting being true or false, starts them up.
I checked which one belonged to the applications I was looking for, and removed them. Logged out, back in, and it's solved.[/COLOR]

However I'm not sure what the desktop files are, and I can't find a directory '.config/autostart/'.

Any ideas?  My problem appears not to be unique.

Thanks.

And I should say, that even when I close all the programs before closing down, they re-start automatically when I log-in - so the desktop immediately becomes cluttered.  There must be some startup file that needs editing, but where is it?

---

### Post by mali2297 on 2007-12-08
> **getmeoutofhere said:**
> 
However I'm not sure what the desktop files are, and I can't find a directory '.config/autostart/'.

Show hidden files (Ctrl+H in Thunar), **.config** is in your home folder.
Remove all files in .config/autostart/, it won't do any harm.

---

### Post by getmeoutofhere on 2007-12-08
Thanks.

I've pressed ctr H like mad, in the .config directory, and no mention of autostart.  In short, I can't find the autostart directory.

The .config directory has four subfolders:

Thunar
mousepad
xfce4
xfce4-session.

(in 6.06 and 7.04).

No autostart.

I would use 6.06 instead of 7.04, but unfortunately I can't get my usb wireless connection to work in the former.   Haven't a clue about 7.10, because on my computer it's so slow as to be unworkabe.  Suffice it to say, I've been doing a lot of  installing!

---

### Post by mali2297 on 2007-12-09
Open the file **.config/xfce4-session/xfce4-session.rc** and see if you can find anything that might be related your problem. Also, remove the content of **.cache** and restart.

---

### Post by Jouke74 on 2007-12-10
Here is the (easier way):

1. Close all your programs when you are going to shut down / log out.

2. Log out your user by clicking on the right icon in the top corner 
(shutdown, log out etc). 

Make sure that the save current session checkbox is re-checked. 

3. Log back into your computer, now your desktop should be clean.

4. Next time when you are shutting down, logging out remove the check at the checkbox.

Edit oops ... did not read well... does this work or not? Otherwise check the list of autostarted applications under the preferences menu, and delete there.

---

