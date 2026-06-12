---
title: "cannot DISABLE visual effects"
date: 2010-12-17
forum: Desktop Environments
---

### Post by stoopkitty on 2010-12-17
*LUCID 10.04 64bit ATI Radeon Mobility X1600:*
Yesterday, I installed a [[COLOR="Navy"]_mac themed skin_[/COLOR]]("http://gnome-look.org/content/show.php/Macbuntu?content=129021") because i wanted to see what it would look like. turns out, after i installed it, i didn't like it, so i uninstalled it. It basically reset all of my visual settings back to their defaults, which was annoying, but i could redo most of them the way i liked it. one of the things that it reset was my appearance preferences->visual effects to normal. 

for some reason, with the visual effects on normal, i started having [[COLOR="Navy"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1467153") problem where there are no window title bars or close buttons etc. i set visual effects to none and the title bars came back but then when i logged out and logged back in, they had disappeared again. i went to appearance preferences and somehow my visual effects were back on normal. 

I thought this might be related to a compiz problem so i reinstalled compiz and now the title bars are there, but they do not follow my theme at all (as shown in attached picture).

i want to use metacity as a window manager(not compiz). everything works just great on the none (visual effects) setting. could this be related to a corrupt preferences file or something? this kept happening on my mac and i just deleted all of my preferences files and it fixed itself but i do not even know where that preferences file would be stored so i'm not sure.

Thanks!!

---

### Post by Kognit on 2010-12-17
Hm. Maybe you should click customize after you click on a theme. And from thereof choose window borders and controls according to the selected theme. 
Maybe it would help you.

---

### Post by 3Miro on 2010-12-17
I have seen this. It has to do with the windows decorations plugin in compiz.

1. Install CCSM (compiz-config-settings-manager) and from the "windows decorations" give it the command:
```
gtk-window-decorator --replace
```
this should make compiz respect your settings.

2. If you want to disable compiz altogether, you should be able to turn off visual effects altogether. If this doesn't work, hit Alt + F2 and type:
```
metacity --replace
```

Post back if this doesn't help.

---

### Post by stoopkitty on 2010-12-17
> **3Miro said:**
> I have seen this. It has to do with the windows decorations plugin in compiz.
.....
Post back if this doesn't help.

Hi, thanks for responding. I tried disabling window decorator, logged out and logged back in, and it got enabled again. this is the same behaviour (not saving settings) that i was seeing with the visual effects settings in apperance. i would set it to no visual effects and it would work, until i logged out and logged back in, when it would switch back to the old settings.

because of this, is it possible it could be a problem with a corrupt or broken settings file or something? if so, how could i fix this? if i delete the file, will the system make a new one and where could i find it?

---

### Post by Krytarik on 2010-12-17
Try deleting the directory "~/.gconf/apps/compiz", that would restore the default settings.

---

