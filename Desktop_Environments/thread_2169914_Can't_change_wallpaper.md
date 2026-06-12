---
title: "Can't change wallpaper"
date: 2013-08-24
forum: Desktop Environments
---

### Post by idovecer on 2013-08-24
Can't change wallpaper in Lubuntu 13.04. Nothing happens if I try via:
1. Preferences -> Desktop preferences -> Select wallpaper, nor
2. using pcmanfm -w some-wallpaper-photo.jpg

I used recently Variety, so maybe there is a problem. Variety is removed and whole varietys configuration but can't change it at all. Also have try to create new user and change wallpaper as new user, nothing, there is default LXDE wallpaper which I can't change ;(.

What causes this problem?

Tnx.

---

### Post by Jonathan Andrew Upton on 2013-08-24
I had this same problem when using Ubuntu: Every time I change the wallpaper, once I shut the computer down and started it up for the next session, the wallpaper will revert back to the default wallpaper. I found that this does not happen with the other default wallpapers that came with the system; it only happens with wallpapers I download from the Web. I assume it could be just a bug, or I am not installing the wallpapers to the system settings properly.

---

### Post by Rex Bouwense on 2013-08-24
I have always used the default wallpaper until I chaged it to the beautiful mountain scene.  I am using Lubuntu 13.04 and it has survived numerous reboots so you must have done something to the file to prevent you from changing it on your system.  
Check this site for additional information:
[http://lxlinux.com/#5](http://lxlinux.com/#5)

---

### Post by hg-knight on 2013-08-26
you could put the downloaded wallpaper into the lubuntu wallpaper folder.open in terminal as sudo .when you restart you will find that it will start up with chosen wallpeper

---

### Post by ankspo71 on 2013-08-29
Have you tried using the full file path of the wallpaper when using the command pcmanfm -w?
Changing the wallpaper without the full path won't work for me. 

working examples:
```
pcmanfm -w "/home/ankspo71/Pictures/Wallpapers/wallpaper12.jpg"
pcmanfm -w "/usr/share/lubuntu/wallpapers/1304-Frosted-Glass_by_Tylana.png"
```

If there is still a problem changing wallpapers then your ~/.config/pcmanfm/lubuntu/pcmanfm.conf file might not exist, or is not usable because it might have become owned by root or marked as read-only. Right click on that file and check the permissions. See screenshot below
[ATTACH=CONFIG]245821[/ATTACH]

I am using Lubuntu 13.04 (32bit) and I am able to change my wallpapers, and it works for me across reboots too,
but the selected wallpaper always appears as "(none)" selected at Lubuntu's desktop preferences for some reason.

---

### Post by idovecer on 2013-08-30
> **ankspo71 said:**
> Have you tried using the full file path of the wallpaper when using the command pcmanfm -w?
Changing the wallpaper without the full path won't work for me. 

working examples:
```
pcmanfm -w "/home/ankspo71/Pictures/Wallpapers/wallpaper12.jpg"
pcmanfm -w "/usr/share/lubuntu/wallpapers/1304-Frosted-Glass_by_Tylana.png"
```


Nope, full path doen't change anything also, simply doesn't work.


> **ankspo71 said:**
> 
If there is still a problem changing wallpapers then your ~/.config/pcmanfm/lubuntu/pcmanfm.conf file might not exist, or is not usable because it might have become owned by root or marked as read-only. Right click on that file and check the permissions. See screenshot below
I am using Lubuntu 13.04 (32bit) and I am able to change my wallpapers, and it works for me across reboots too,
but the selected wallpaper always appears as "(none)" selected at Lubuntu's desktop preferences for some reason.

I do have this pcmanfm.conf file in this path, and there is defined another wallpaper which OS doesn't select. Also, I have try to remove this file, to leave conf file empty, to change to chmod 777, nothing.

It doen't simply work.

I can only change wallpaper in Desktop Preferences (there is always none), but after selecting new Wallpaper and after restart Lubuntu, wallpaper is changed :). In desktop preferences as Wallpaper is still none :).

---

### Post by Dennis N on 2013-08-30
I changed mine by creating a symbolic link from lubuntu-default-wallpaper.png (the default selection in the Desktop Preferences - it shows 'none' in the box) to one I wanted to use. That might work.

Use terminal, and cd to the wallpaper directory:

**cd  /usr/share/lubuntu/wallpapers**

Suppose I want to change my wallpaper to: 1304-Nature_by_wakarii.jpg (one of the choices in there)

Command to create symbolic link to desired wallpaper:

**sudo ln -sf 1304-Nature_by_wakarii.jpg lubuntu-default-wallpaper.png**

Leave the selection in the Desktop Preferences set to lubuntu-default-wallpaper.png

Log out and Log in to see the change.

This will revert the change made above back to the original default:

**sudo ln -sf 1304-default-particule.png lubuntu-default-wallpaper.png**

(You can also add other images into that directory for use as the wallpaper.)

---

