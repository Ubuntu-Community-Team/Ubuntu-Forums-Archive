---
title: "Replaced GDM with KDM ... other opinions?"
date: 2009-11-17
forum: Desktop Environments
---

### Post by scorp123 on 2009-11-17
The impossibility to theme the new GDM in any *reasonable* way (I am aware of the workarounds such as "gksudo -u gdm dbus-launch gnome-appearance-properties" -- but I said: "reasonable" ...) really got on my nerves. Seriously. WTF? How could they release Ubuntu 9.10 with such a regression from 9.04 ... ??

I tried using the GDM legacy package "**gdm-2.20**" but running the old GDM failed totally due to the absence of several needed config files.

So I got rid of GDM and I installed KDM ...
```
sudo apt-get install kdm systemsettings
```

This of course will pull in some KDE libs as dependencies ... but OK. Nothing too dramatic.

So now when I execute the "System Settings" application and go to the "Advanced" section I can configure the KDM login screen with ease and also easily theme it as I wish:
```
gksudo systemsettings
```

KDM seems way faster than GDM. When I use GDM on my old "CoreDuo" (= 32-bit) laptop it would display that stupid brown "Cylon" (= the robots from the "Battlestar Galactica" SciFi series with their blinking red eye -- that splash screen certainly looks as if one of those guys was looking at you, LOL ... ) splash screen for waaaay too long both before showing the login mask and before actually loading the chosen desktop environment. From that point of view Karmic has turned out to be SLOWER for me than Jaunty was.

Now with KDM I finally got some speed back and that stupid "Cylon" splash screen is gone.

Any opinions on this? Is replacing GDM with KDM really the only reasonable way to get an easily themable login screen again??

Or is there anyone who was succesful in getting "gdm-2.20" to work with Karmic?

---

### Post by ZoiaGuyver on 2009-11-18
This has been said about a lot... it seems with the GDM rewrite it left the new GDM with no accessible theme's preferences yet. I've hunted around and it seem's till the GDM is actually updated with the settings panel's there is no real "easy way" of doing it.

The new GDM has it's advantages but the are more core than feel or looks.

Till they update GDM i would stick with KDM tbh.

---

### Post by ZoiaGuyver on 2009-11-18
Erm almost a double post..

---

### Post by scorp123 on 2009-11-19
I found a way to downgrade GDM ....  I'll place it into a separate thread.

EDIT:

Here is the link:
[http://ubuntuforums.org/showpost.php?p=8350408&postcount=2](http://ubuntuforums.org/showpost.php?p=8350408&postcount=2)

I sucessfully downgraded the new GDM and now I have the same good old themable GDM as on Jaunty again.

---

### Post by plenthoz on 2011-01-18
sir i've tried this but after i reboot and login i've got nothing but a console...can you help me??

thanks a lot sir

---

### Post by scorp123 on 2011-01-19
> **plenthoz said:**
> sir i've tried this but after i reboot and login i've got nothing but a console...can you help me??

You do realise that this is an old thread and that the instructions were therefore written for an older Ubuntu release? And you shouldn't follow instructions blindly if you don't know what you are doing.

If you only have console now, login in text mode and try to get gdm back:

```
sudo apt-get --purge remove kdm
sudo apt-get --reinstall install gdm

```

Please note that the password is never ever echoed back. Whenever you type a password (e.g. on the login screen; or when using "sudo") the system will not respond with anything. Silent blackness is all that you will get. Just type your password blindly and hit enter. If you typed it correctly the system will do what you said. If you mistyped it, the system will complain. In that case try again.

---

### Post by plenthoz on 2011-01-19
hehehe thanks a lot sir i've just figure it out to make gdm as default by dpkg-reconfigure command:p


i'm using ubuntu 10.10 sir what do you suggest to make the login screen themable

thank you

---

### Post by plenthoz on 2011-01-19
hehehe thanks a lot sir i've just figure it out to make gdm as default by dpkg-reconfigure command:p


i'm using ubuntu 10.10 sir what do you suggest to make the login screen themable

thank you

---

### Post by plenthoz on 2011-01-19
hehehe thanks a lot sir i've just figure it out to make gdm as default by dpkg-reconfigure command:p


i'm using ubuntu 10.10 sir what do you suggest to make the login screen themable

thank you

---

