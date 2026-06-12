---
title: "making Login Managers"
date: 2006-01-23
forum: Desktop Environments
---

### Post by leveliv on 2006-01-23
hi Im using GNOME and im wondering how to make a Login Manager 

[http://art.gnome.org/themes/gdm_greeter/91]("http://art.gnome.org/themes/gdm_greeter/91")

---

### Post by bernardfrancois on 2006-01-25
I wonder how to do that too.
I tried to google it but I didn't find anything useful.

I checked *man gdmsetup* (the utility that allows you to change the login manager), and I found that **/etc/X11/gdm/gdm.conf** is the file where all those settings are saved. Maybe from there you can find the location of the other login screens. You could try to find out how they work, and then make your own...

If you find out more, please post it here.

---

### Post by aysiu on 2006-01-25
How to make a login manager theme? Is that what you're talking about?

Alt-F2
```
gksudo nautilus
```
Go to /usr/share/gdm/themes/
Copy a theme that's there.
Then modify the pictures inside of it to be what you want.

---

### Post by leveliv on 2006-01-26
no I dont htink thats what we meant...like in windows there is Login Studio I think to make XP Logons ...all these GDMs must have started with something...some kind of program unless someone did all the coding and stuff with a text edit program

---

### Post by ardchoille on 2006-01-26
Most of the login screens can be made by simply copying an existing one, changing aspects of it (chaning/adding pictures, editing the xml, etc) and then repackaging it. Seriously, I have made tons of these themes and I start out by copying an existing theme. If you want to make one from scratch I suggest you learn xml to write the xml file and add your own pictures, that's really all there is to it.

Once you have your theme made, install it. Then log out, press CTRL+ALT+F1 to get to a VT, then enter the below command to get a screenshot of the login screen on VT7:

```

chvt 7 ; sleep 5 ; XAUTHORITY=/var/lib/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/screenshot.png

```

Once you have your screenshot, simply put it in the theme folder, repackage and reinstall. Then, you're done :)

I have searched for two years to find a "login studio" type of app for Linux and I never found one - probably because it's so easy to make one without such an app.

---

