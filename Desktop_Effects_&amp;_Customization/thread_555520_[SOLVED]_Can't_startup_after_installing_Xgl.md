---
title: "[SOLVED] Can't startup after installing Xgl"
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by kittykatzejager on 2007-09-20
Help me please! 

I tried to get Beryl running on Ubuntu, and now can't boot in to Ubuntu anymore. I put Feisty on my Acer - as a dual boot with Vista (Home Premium).

I followed the instructions at [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)  (Method B, ATI with fglrx drivers) to get xgl working with ATI. I didn't get to installing Beryl. 

Ubuntu seems to be starting up, but just doesn't get to the login screen.

In recovery mode, there is a black screen that runs through a whole lot of processes, then it stops at some lines that say:

[FONT="Courier New"]Error: Microcode "bcm43xx_microcode5.fw" not available or load failed. firmware_helper [4472]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:00.0' with driver '(unknown)'[/FONT]

And these lines repeat every minute or so.

I don't know what I should do.  Is there a way to undo the changes I made?? 

Any help would be very much appreciated. Thanks.

---

### Post by praet on 2007-09-20
You will have to undo the changes made to gdm.conf.
If you can get the system booted at all and you can switch to a new shell using Ctrl+Alt+F1, then you can login and make the changes from the terminal.  
```
sudo nano /etc/gdm/gdm.conf
sudo nano /etc/gdm/gdm.conf-custom
```

If not, then you may be able to make the changes by booting from the ubuntu livecd.

---

### Post by kittykatzejager on 2007-09-20
Thank you for your reply. 

I will try that and get back. Japan time 3am... 

Much appreciated.

---

### Post by kittykatzejager on 2007-09-20
That worked perfectly. Had a little trouble navigating my way around nano - Guess I had better learn the basics before I go editing files next time.

Thanks so much for your help!

---

### Post by praet on 2007-09-21
No problem.

If you had problems with nano there are a slew of excellent command line text editors out there.  

For the next attempt, I recommend method "A" on that guide, as it will add a new login session entry that you can optionally select from the login screen to try out.  That way if it doesnt load properly, you simply log out (ctrl+alt+backspace) and select the default Gnome login session.  

Then when you get it working, you can default the new Xgl session.  

Heres a rundown:
```
gksudo gedit /usr/bin/startxgl.sh
```
basically, create a script at **/usr/bin/startxgl.sh** and put this in it:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session
```

Then make it executable: 
```
sudo chmod +x /usr/bin/startxgl.sh
```

Then create a session option that calls the script you just created:
```
gksudo gedit /usr/share/xsessions/xgl.desktop
```
with this text:
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```

You can also start compiz or beryl in the startxgl script as well.

---

