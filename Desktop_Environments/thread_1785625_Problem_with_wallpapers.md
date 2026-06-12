---
title: "Problem with wallpapers"
date: 2011-06-18
forum: Desktop Environments
---

### Post by antoniu86 on 2011-06-18
Hi,

I have a very stupid problem with wallpapers. I tried to put some wallpapers, that i used before re-installing my Ubuntu, in the background folder from usr/share. after putting them i couldn't use them. don't know why. first time i installed ubuntu 11.04 it worked great. i used the "sudo nautilus" cmd in terminal in order to have the admin acces. now the only way to put them in the background folder i by using the "sudo mv ..." cmd. with this it works to change the desktop wallpaper but it doesn't work to change the login screen background. it is very strange. 

i also have this error when starting nautilus with sudo:


Initializing nautilus-gdu extension
Initializing nautilus-dropbox 0.6.7

** (nautilus:10035): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '10035'

(nautilus:10035): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


Can any one help me?

---

### Post by TheDoctorX on 2011-06-18
try to reboot ... maybe  the nautilus gave error and blocked ... if the problem persist try update the nautilus manager through the update manager...

---

### Post by antoniu86 on 2011-06-18
i reinstalled nautilus and everything about it ... and now it's working. but with the wallpaper probelm i don't understand a thing. when i move them with nautilus i can't use them and when i move them in terminal cmd it works, but still can't use them to change the login screen background. i thought that the error from nautilus is the problem.

---

### Post by Krytarik on 2011-06-18
Make sure the permissions are set correct, so that everyone can read the image.

Greetings.

---

### Post by antoniu86 on 2011-06-19
I managed to crash it :D. i think it was better this way because i installed it again and now it works fine. sometimes is faster to re-install it than to fix all the mistakes.

---

