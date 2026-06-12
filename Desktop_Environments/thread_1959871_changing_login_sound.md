---
title: "changing login sound ?"
date: 2012-04-16
forum: Desktop Environments
---

### Post by CaesarDeb on 2012-04-16
Hello all I`m not really a linux newb but I have a quick question.
I thought I changed the login sound correctly but still no sound.

I did this in this order 

cd /usr/share/sounds/ubuntu/stereo 

sudo rm desktop-login.ogg 

and it removed than I cd out into home 

mv desktop-login.ogg /usr/share/sounds/ubuntu/stereo 

and rebooted and had audio loud and still no sound.
Do I need to make it executable first if so which one ?
Also the login sound is just 30sec and 1.1mb if thats the problem.

Thanks

---

### Post by Lemuriano on 2012-04-16
Hi,

This work like a charm. 

Disable or Change Login Sound Each time when you login to Ubuntu, it plays a login sound. If you  don't like to listen to it each time you login, you can easily disable  it, or you can even change it to your favorite sound.
 To disable the login sound:
 
[LIST=1]
[*] 		Go to System > Preferences > Startup Applications.
[*] 		Under the "Startup Programs" tab, untick "GNOME Login Sound"
[*] 		Click Close
[/LIST]
  To change the login sound, tick the above "GNOME Login Sound" if it's unticked, then follow these steps:
 
[LIST=1]
[*] 		Press Alt+F2 to bring up "Run Application" window.
[*] 		Paste [COLOR=#0000FF]gksu nautilus /usr/share/sounds/ubuntu/stereo[/COLOR] into the box, click "Run" to open Nautilus in the right folder.
[*] 		Rename the original file [COLOR=#0000FF]desktop-login.ogg[/COLOR] to another such as [COLOR=#0000FF]desktop-login-original.ogg[/COLOR] for backup
[*] 		Copy your sound file in ogg format to the above folder and name the file as [COLOR=#0000FF]desktop-login.ogg[/COLOR]
[*] 		Log out and log back in to listen to the new login sound.
[/LIST]
Regards.

---

### Post by CaesarDeb on 2012-04-16
Yeah it still gets me nothing I try again later thanks

---

