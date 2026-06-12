---
title: "How to get login sound back"
date: 2014-02-13
forum: Desktop Environments
---

### Post by elim-qiu on 2014-02-13
I have two Ubuntu 13.10 installed to two laptops of the same brand.

One plays login sound and one doesn't (although there is sound of drums at the login prompt)

I don't know why there is such a difference. Just to make sure a correct installation, I'd like to get the login sound back.

Adding a record in start up list  does not working, it says file not found. I wonder if there is a re-install of some pkg can fix it, say, using Synaptic pkg manager?

---

### Post by deadflowr on 2014-02-13
Open the program "Startup Applications" and add this command
```
canberra-gtk-play  --file <file/name/here>
```
then save or close and it should have whatever sound you picked at startup.
You can test that the command works by running it in a terminal.

The old Ubuntu sound should be set in a different place
/usr/share/gnome/autostart/libcanberra-login-sound.desktop
in this file change the line
X-GNOME-Autostart-enabled=false
to
X-GNOME-Autostart-enabled=true

See if that works.

---

### Post by buzzingrobot on 2014-02-14
Exact same speakers?    I had a machine with speakers that "slept" to save energy.  I wouldn't hear login sounds because they took too long to wake up.

---

### Post by Frogs Hair on 2014-02-14
The old method of adding the sound to start up applications didn't work for me in 13.10 .  The sound has been disabled by default since 12.04 but the sound is still in the usr/share/sounds folder. I think it's named desktop-login.ogg  . I had enablded the sound  in 12.04 with the dconf editor, but this method doesn't  work on my 12.04.4 installation. There was a instruction for creating a very simple script to be added to start-up applications , but I haven't been able to locate it yet .


Edit: Success with 12.04.4  and 13.10 . Open dconf editor and proceed to org > gnome > desktop > sound and make sure sound is set to default , then add the start-up command at the link and restart.    

[http://www.ubuntugeek.com/how-to-enable-startup-login-sound-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-enable-startup-login-sound-in-ubuntu-12-04-precise.html)

---

### Post by speartip on 2014-02-15
```
[SIZE=2][COLOR=#000000][FONT=Ubuntu]gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop[/FONT][/COLOR] [/SIZE] 
```
Then change autostart enabled to true, & save the file.
Log out & back in again, & you should have login sound back.

---

### Post by elim-qiu on 2014-02-18
> **speartip said:**
> ```
[SIZE=2][COLOR=#000000][FONT=Ubuntu]gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop[/FONT][/COLOR] [/SIZE] 
```
Then change autostart enabled to true, & save the file.
Log out & back in again, & you should have login sound back.
[COLOR=#000000]Thanks speartip! [/COLOR]Great solution!

---

