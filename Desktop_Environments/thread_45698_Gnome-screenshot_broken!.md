---
title: "Gnome-screenshot broken!"
date: 2005-07-01
forum: Desktop Environments
---

### Post by Avianca757 on 2005-07-01
Hi!:

I logged today at my ubuntu system as usual, and was going to take an screenshot to send to a friend and I got:

The Application "gnome-screenshot" has quit unexpectedly.

I get this error via the Gnome menu or via the print screen key.
Can anybody suggest me a way to work this around?
I'm a newbie!

Thanks

---

### Post by intangible on 2005-07-01
I would start "gnome-screenshot" from a terminal and then try a screenshot to see what error message it gives when it crashes.

A work around would be to use "gimp" to get your screenshot.  In the gimp, the option is under "File->Acquire->Screen Shot".

---

### Post by Avianca757 on 2005-07-01
I get this when running on terminal

andres@ubuntu:~$ gnome-screenshot
Xlib:  extension "SHAPE" missing on display ":0.0".

Do you know what can it be?

I was able to acquire the image via The Gimp as well, thank you very much!

---

### Post by intangible on 2005-07-01
Perhaps a misconfiguration in /etc/X11/xorg.conf       want to post that here so I can take a look?

---

### Post by Avianca757 on 2005-07-02
Here it is!

---

### Post by intangible on 2005-07-03
If you remove 	**Option		"UseFBDev"		"true"**  does that seem to make a difference?  Everything else looks completely normal, that's the only think I could think might make a difference.

Do this also: **cat /var/log/gdm/\:0.log** and post that as well.

---

### Post by varunus on 2005-07-03
Also, can you post your /var/log/Xorg.0.log file?  Maybe the shape extension is having an error when it loads...

---

