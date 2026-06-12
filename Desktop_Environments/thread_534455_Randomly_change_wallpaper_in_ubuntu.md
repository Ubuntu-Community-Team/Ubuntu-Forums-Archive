---
title: "Randomly change wallpaper in ubuntu"
date: 2007-08-25
forum: Desktop Environments
---

### Post by vsayikiran on 2007-08-25
i need a software like webshots in windows OS that can change wallpaper frequently. Does any body now how to cycle wallpapers automatically in ubuntu v7.0.4 GNome . i also want to know in which folder does current wallpaper is stored.

---

### Post by Happy_Man on 2007-08-25
You can use wallpaper-tray (in the repos).

---

### Post by ecr959 on 2007-08-25
Hello Vsayikiran

        Right now, I'm using Ubuntu, but a few months ago, I was using Kubuntu,  which is actually the very same, except you have KDE on the desktop.   And KDE allows you to tweak desktop wallpaper, you can pick the images, and tell it to do "slideshow"   that is what you are asking for.   I'm not a ubuntu guru, but if it can be done in Kubuntu, then it should not be too hard in Ubuntu.

I wish I could be more precise, but at least now you know it can be done.
Good Luck:)

---

### Post by vsayikiran on 2007-08-25
i have downloaded n installed wallpaper tray package , but i dont know how to launch it. even the notification area does not contain any icon form where i can access wallpaper tray. does anyone has solution for this.

---

### Post by EvergreyNY on 2007-08-25
i just installed it to check it out

from terminal, run ```
wallpaper-tray
```

you should now have an icon of your current wall in the tray. a preferences dialog box should appear as well. add the directories containing the walls that you want to use. edit other options as well under 'More Options'

once again, from the terminal, run ```
gnome-session-properties
```

under the 'Startup Programs' tab create a new entry titled 'Wallpaper Tray' and use the command [FONT="Courier New"]**wallpaper-tray**[/FONT]

EDIT:
alright, just tried it out and everything seems to work properly. im not 100% sure where the default wallpapers are stored, I just store them in a folder in Home

---

### Post by Dwiman89 on 2007-09-05
Will wallpaper tray work well with Beryl? Hambone

---

### Post by ecr959 on 2007-09-30
Hello Vsayikiran

            I just wanted to tell you that after today's bunch of updates, I now have wallpaper tray in my Applications / graphics dropdown list.  Just configure it to a particular folder, then put all the wallpapers you want to see , in that folder.  

I told it to pick Random wallpapers, and I told it to change it every 2 minutes.    And it works great.

---

### Post by rude_lee on 2008-07-15
cool nice feature it still works

---

