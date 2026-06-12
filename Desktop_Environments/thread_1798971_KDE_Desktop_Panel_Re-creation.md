---
title: "KDE Desktop Panel Re-creation"
date: 2011-07-06
forum: Desktop Environments
---

### Post by SunfireSSR on 2011-07-06
New to the KDE plasma Desktop.I deleted the original desktop panel on my desktop. How do I re-create it. I deleted it when I thought I was deleting (1) of (6) WeatherLCD widgets I put on it not knowing what I was doing. Thanks in advance...

---

### Post by Alwimo on 2011-07-06
I'm a bit rusty with KDE, but:
 
Right-click on the wallpaper and choose 'New Panel'.
 
Or if you mean the translucent "Desktop" plasmoid: right-click, choose new plasmoid, choose 'Folder View'.

---

### Post by SeijiSensei on 2011-07-07
If you don't mind starting from scratch, reboot into "recovery mode," then 

```

cd /home/username
mv .kde .kde.bad

```

Reboot.  Now KDE will rebuild your desktop with the defaults.  If you haven't invested much in desktop themes, backgrounds, etc., this is the easiest and fastest solution.  By renaming your old directory to .kde.bad you can always copy over files from your old configuration if you know what you're looking for.

---

### Post by ankspo71 on 2011-07-07
Hi,
It is like Alwimo said, but if you locked your widgets after you accidentally deleted your panel... you will first need to unlock the widgets by right clicking on the desktop and choose "unlock widgets". Then the "add widgets" and "add panel" will appear in the right click menu when you right click on your desktop.
Hope this helps.

---

### Post by SunfireSSR on 2011-07-07
The only recovery mode I know of is the Gnome Recovery at the login screen. I installed the KDE Plasma desktop on Ubuntu 10.04.

So, correct me if I'm wrong, I should be able to do the following:
Log into the Gnome Desktop.
Open a terminal window.
Run the commands listed above.
Logout of the Gnome Desktop.
Log back into the KDE Desktop.
Shazam !!!   (LOL !!!)

---

### Post by SunfireSSR on 2011-07-08
Well, I can't find the .kde directory. It does not exist in my home directory.

---

### Post by lykwydchykyn on 2011-07-08
If you have any saved KDE configurations coming up, you do have a .kde directory.  Remember that files beginning with '.' are hidden.

But you shouldn't need to do all that just to get back the default panel.  Just right click the desktop and "add panel", one of the choices should be "default panel".

---

### Post by SunfireSSR on 2011-07-09
Thanks for the "." info. I wasn't sure if it was hidden, but it took the commands and the desktop is back to it's original look. Now to figure out why I can't see the LCD Weather widget. I added one only this time, but it hasn't shown up. 

Thanks Again for your help everyone !!!

---

