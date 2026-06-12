---
title: "Annoyances after installing KDE"
date: 2006-08-25
forum: Desktop Environments
---

### Post by EvergreyNY on 2006-08-25
Gnome was been working fine until I installed KDE last night (through apt-get). Now, the volume controls on my keyboard don't work and when I manually change the volume from the menubar, it works opposite of what it should (pressing + dcreases the volume and vice-versa).

---

### Post by linuxguy on 2006-08-25
if you really want to use KDE, get kubuntu

---

### Post by EvergreyNY on 2006-08-25
> **linuxguy said:**
> if you really want to use KDE, get kubuntu

I honestly can't stand KDE, it's just that I have a few programs that really only work in it.

---

### Post by fakie_flip on 2006-08-25
You can use KDE programs without KDE. I am using Amarok and K3B in Gnome. You will have to get some graphics libraries, but you won't need to download as much you did installing the full KDE.

---

### Post by ash211 on 2006-08-25
> **EvergreyNY said:**
> Gnome was been working fine until I installed KDE last night (through apt-get).

Which did you apt-get install: kde or kubuntu-desktop?

---

### Post by linuxguy on 2006-08-25
> **EvergreyNY said:**
> I honestly can't stand KDE, it's just that I have a few programs that really only work in it.

Ah ok. I suggested Kubuntu because I liked that experience more than the Ubuntu + KDE one (I've tried them both). But in the end, I prefer GNOME as well.

---

### Post by EvergreyNY on 2006-08-25
> **ash211 said:**
> Which did you apt-get install: kde or kubuntu-desktop?

kubuntu-desktop

---

### Post by EvergreyNY on 2006-08-25
Alright, after simply removing the applet and adding it again, the volume moves the correct way. Now only my e-mail and web browser buttons are working out of all the media buttons on the keyboard. I'm using a Logitech Media Elite (the version before the current one, PS/2)

[http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2166,CONTENTID=10568](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2166,CONTENTID=10568)

All of the keys had been working fine off a clean install of Ubuntu until this mini fiasco.

---

### Post by ash211 on 2006-08-25
I would suggest running the few KDE apps you need from inside GNOME instead of switching to KDE if it's breaking your keyboard buttons.  What apps are you trying to run?  Do these keyboard errors occur while you are still in GNOME?  

Also, in case we need to [file a bug in launchpad]("https://launchpad.net/distros/ubuntu/+bugs"), could you please provide your keyboard's model and the results of ```
uname -r
```  Thanks

---

### Post by sawjew on 2006-08-25
Try keytouch to enable all your keys.  It should work whatever desktop you are using and it has a preset profile for the Logitech Media Elite.  If you want to change anything or set up your own shortcuts it's very easy using the keytouch editor.  I just got all the hotkeys on my Compaq Evo laptop working under Xubuntu in about 5 minutes.  Available from [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/).

---

### Post by EvergreyNY on 2006-08-25
After a little doodling, I got all the media keys working again. It appears as if KDE, for some reason, changed the keyboard layout to a standard 104-key set. With Keytouch, I was able to get everything back to normal functionality.

---

