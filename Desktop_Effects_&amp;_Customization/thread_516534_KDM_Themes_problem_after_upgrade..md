---
title: "KDM Themes problem after upgrade."
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by upthelum on 2007-08-03
I just upgraded from 6.6.1 to version 7.0.4 in two steps from dapper to edgy then to fiesty (perhaps feisty first i'm not sure), using KDE and seem to have a problem with KDM theme manager. It's moved position in system settings, which is fine but, when i go into it i cant select or change any themes, i cant do anything. It says to use administrator mode but the button isn't there. Can anyone help?

Also i installed compiz from Synaptic but it doesn't seem to have installed at all, where do i find it if it installed, is it supposed to put an icon in system tray etc?
Help!!!

---

### Post by upthelum on 2007-08-03
Can someone suggest a solution???

---

### Post by lobo_cobra on 2007-11-10
Same problem. Can not change theme of KDM... I am going to try to do it manually now... 
I will post if i have success

---

### Post by lobo_cobra on 2007-11-10
>> **lobo_cobra said:**
> Same problem. Can not change theme of KDM... I am going to try to do it manually now... 
>I will post if i have success

Ok, after a few trials, I got it working, changing the theme manually. I can confirm, that the automatic change with kcontrol does currently not work. Procceed as follows to change theme in Gutsy until the bug is fixed:

 sudo vim /etc/kde3/kdm/kdmrc
  #search for "Theme=" and change it to:
  Theme=/usr/share/apps/kdm/themes/[name of the dir of your new theme]/
  #!!! add following key 
  UseTheme=true

restart kdm
enjoy...

P.S. maybe someone test first only to insert "UseThme=ture". I think only this key was missing. Please post if you have success or proceed as I described here.

---

