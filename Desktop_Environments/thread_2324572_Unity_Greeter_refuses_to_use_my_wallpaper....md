---
title: "Unity Greeter refuses to use my wallpaper..."
date: 2016-05-14
forum: Desktop Environments
---

### Post by exploder on 2016-05-14
I installed Ubuntu 16.04, at first I used one of the default wallpapers. Later, I found a wallpaper on-line but the greeter will not us it and is stuck on the default wallpaper with the bubble.... The greeter refuses to use any other wallpaper including any other of the defaults! How the heck do I fix this?

---

### Post by CantankRus on 2016-05-14
Did you edit any files or just use the **Settings > Appearance** gui ?

What is your terminal output from...
```
gsettings get com.canonical.unity-greeter background
gsettings get com.canonical.unity-greeter draw-user-backgrounds
```

---

### Post by exploder on 2016-05-15
> 

    Did you edit any files or just use the Settings > Appearance gui ?

I used Settings, Appearance. 

> 
What is your terminal output from...

> $ gsettings get com.canonical.unity-greeter background
'/usr/share/backgrounds/warty-final-ubuntu.png'


> gsettings get com.canonical.unity-greeter draw-user-backgrounds
true


Looks like it should work but it doesn't....

---

### Post by CantankRus on 2016-05-15
What's the "default wallpaper with the bubble"? pic

The way to set how the greeter wallpaper behaves is through configs in **/usr/share/glib-2.0/schemas/**
eg
my file **/usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override** contains...
```
[com.canonical.unity-greeter]
draw-user-backgrounds=false
background='/home/glen/Pictures/wallpaper/wisp.png' 
```
which sets  the greeter to always draw "/home/glen/Pictures/wallpaper/wisp.png" as the greeter background.
Do you have any such override file?

PS: If you edit any override files you must then run....
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

---

### Post by mc4man on 2016-05-15
Otherwise - 
At least here what's in dconf doesn't matter, it's just a fallback.
If still stuck maybe - 
Copy an image you want to ~/Pictures, then pick it & see if used at greeter.
If not then there are 2 folders, ck. the permissions of the folders & the file inside of each folder. Screenshot is self explanatory

---

### Post by exploder on 2016-05-15
All my permissions are identical. The lock screen uses my wallpaper, the greeter still will not. I even went so far as to do another clean install this morning, still no change....

---

### Post by mc4man on 2016-05-15
What was mentioned in post 4 should work except it may need to be done again if switching. 
Can you compress to a .gz the image you're using & attach to a post?
Also try this attached image, it's a simple gradient I use here (gradients can not be used as the greeter screen so I converted to a .png which can.
If you were to extract 1.png, put it in the  Pictures folder, set as background & log out, - is it used on the greeter?

If you keep getting the same undesired image then do this - 
```
sudo rm /var/log/lightdm/x-0-greeter.log
```
log out/in, after logging in, - 
```
sudo cat  /var/log/lightdm/x-0-greeter.log
```
copy out what's shown & post

---

### Post by exploder on 2016-05-16
I did another clean install on my father-in-law's computer and found it had the exact same problem! Also, saw another user on-line experiencing this as well. For now the greeter is using the default wallpaper and I can live with that until hopefully an update fixes it.

---

### Post by CantankRus on 2016-05-16
FYI I just did a fresh install of 16.04 and by default the greeter uses the desktop wallpaper of each selected user.

---

### Post by mc4man on 2016-05-17
> **exploder said:**
> I can live with that until hopefully an update fixes it.
That's not going to happen as for 99.99% of ubuntu session users this is not an issue. You fail to provide any add. info as requested here & in ask ubuntu, so too bad..

---

### Post by exploder on 2016-05-17
I appreciate the help but today I just plugged the drive back in with Ubuntu Mate. I have so much going on right now that my desktop is the least of my problems.

---

