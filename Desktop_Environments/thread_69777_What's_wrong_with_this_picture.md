---
title: "What's wrong with this picture?"
date: 2005-09-27
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-09-27
I'm logged into xfce, but it has a gnome desktop. What gives?

I think I'll just re-install ubuntu, it's been acting up too often lately, especially with XFCE...

---

### Post by 23meg on 2005-09-27
is nautilus running?

---

### Post by YourSurrogateGod on 2005-09-27
[QUOTE=23meg]is nautilus running?[/QUOTE]
Yes.

---

### Post by YourSurrogateGod on 2005-09-27
I turned nautilus on and off, the desktop seems to have vanished, but I can't change my wallpaper... wtf?

---

### Post by YourSurrogateGod on 2005-09-27
And now Gnome is screwy. Whenever I open a window, it doesn't show up below...

[edit]

Ok, got the window list back...

---

### Post by 23meg on 2005-09-27
you should run nautilus only if you want the gnome desktop. 

what happens when you try to change your wallpaper?

---

### Post by YourSurrogateGod on 2005-09-27
[QUOTE=23meg]you should run nautilus only if you want the gnome desktop.[/quote]
2 questions...

1) What do I use when I'm in xfce for a GUI in order to look at my files?
2) How do I make sure that Nautilus does not start up when I log into XFCE?
[quote=23meg]what happens when you try to change your wallpaper?[/QUOTE]
Absolutely nothing. I select the wallpaper and the old one remains.

---

### Post by 23meg on 2005-09-27
1) you use the rox file manager. just type rox at the terminal if you can't find it elsewhere.

2) it's strange that it's started without you deliberately starting it. just make sure nautilus isn't selected as a startup app in your xfce session (i forgot how to set this since i haven't used xfce in a long time; you should know better)

for the wallpaper problem, try manually starting xfdesktop once you've killed nautilus.

---

### Post by YourSurrogateGod on 2005-09-27
> **23meg]1) you use the rox file manager. just type rox at the terminal if you can't find it elsewhere.

2) it's strange that it's started without you deliberately starting it. just make sure nautilus isn't selected as a startup app in your xfce session (i forgot how to set this since i haven't used xfce in a long time said:**
> 
I don't 8-[ . I'm still getting the hang of it after a slew of problems that I've encountered with it...
[quote=23meg]for the wallpaper problem, try manually starting xfdesktop once you've killed nautilus.
Thanks...

Is there a complete manual for xfce somewhere?

---

### Post by YourSurrogateGod on 2005-09-27
Oh yeh, rox, I know remember it. I couldn't stand that thing since every time I moved to a different folder, the darn thing would simply resize. And opening some files was simply a pain with it.

---

### Post by YourSurrogateGod on 2005-09-27
Ok, the sessions seem to be configured ok. So gnome apps shouldn't start up when I log into xfce again...

---

### Post by ygarl on 2005-09-28
Annoyingly, this has happened in every distro when I run XFCE. 

Also happens in IceWM as well - you end up with Gnome menus when you right-click on the desktop instead. I just went <shrug> and installed another file manager for when I want to use one on Xfce and IceWM.

---

### Post by foxy123 on 2005-09-28
What you have to do is the following:

1. killall nautilus in console
2. Run xfdesktop in Run Programme (or I guess xfdesktop & in console)

Make sure that you session settings are saved on exit. Quit xfce and log in back. You should have all this sorted.

3. Next time if you run nautilus, use "--no-desktop" option. Alternatively go to Configuration Editor/apps/nautilus/preferences and untick Show Desktop to get rid of it for good.

---

### Post by drummer on 2005-09-28
If you want to run nautilus in xfce, just as a file manager, start it with the --no-desktop flag and it won't steal the desktop from xfdesktop.```
nautilus --no-desktop
```
EDIT - beat me to it, foxy123 :P

---

### Post by YourSurrogateGod on 2005-09-28
Heh... thanks. After some hacking, I managed to get it to work.

---

### Post by psychicdragon on 2005-09-28
Remember to tell nautilus not to take over the desktop anymore:
```
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false
```This way you can still use nautilus for file management if you like.

---

### Post by YourSurrogateGod on 2005-09-28
[QUOTE=psychicdragon]Remember to tell nautilus not to take over the desktop anymore:
```
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false
```This way you can still use nautilus for file management if you like.[/QUOTE]
Thanks.

I unchecked the check-box in sessions and settings that said that gnome apps should start whenever I log into xfce, so I think that did the trick.

---

### Post by psychicdragon on 2005-09-28
That's something else. I'm not sure exactly what it starts up when you have that checked.

When ever you run any Gnome app it seems to spawn a bunch of processes like:
bonobo-activation-server, dbus-daemon-1, dbus-launch, gam_server, gconfd-2

So maybe it's that stuff?

---

### Post by YourSurrogateGod on 2005-09-28
[QUOTE=psychicdragon]That's something else. I'm not sure exactly what it starts up when you have that checked.

When ever you run any Gnome app it seems to spawn a bunch of processes like:
bonobo-activation-server, dbus-daemon-1, dbus-launch, gam_server, gconfd-2

So maybe it's that stuff?[/QUOTE]
Probably, because after I fixed all of that, I don't have any problems.

---

