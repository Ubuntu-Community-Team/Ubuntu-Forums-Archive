---
title: "system retore in ubutu"
date: 2007-07-12
forum: Desktop Effects &amp; Customization
---

### Post by Balvinder25 on 2007-07-12
hi all,
          one of the things that i really miss in ubuntu is system restore.like the one in Xp..isnt there any way how we could have that in ubuntu and one more question for some strange reason ubuntu has stopped mounting my c partition ???i :( ..itried creating a script in the /etc/anacron file 

sudo mount /dev/hda1 /media/hda1

but its not there when i resstart the pc ..but the same command works if i type it in console??

if any one could help  me on this..?that would really great.


Balvinder singh

---

### Post by Paul820 on 2007-07-12
If that is a windows drive you need ntfs-3g to mount it at boot. You can get it through synaptic or from the terminal: sudo apt-get install ntfs-3g

---

### Post by amadeus266 on 2007-07-12
If they can create something like system restore in Ubuntu, it would definitely have to be better than windows xp. The one in windows doesn't really work very well.

---

### Post by NullHead on 2007-07-12
> **Balvinder25 said:**
> hi all,
          one of the things that i really miss in ubuntu is system restore.like the one in Xp..isnt there any way how we could have that in ubuntu and one more question for some strange reason ubuntu has stopped mounting my c partition ???i :( ..itried creating a script in the /etc/anacron file 

sudo mount /dev/hda1 /media/hda1

but its not there when i resstart the pc ..but the same command works if i type it in console??

if any one could help  me on this..?that would really great.


Balvinder singh

You might want to edit the fstab file located in /etc/fstab.lst .

---

### Post by Balvinder25 on 2007-07-12
thanks for teh quick response guys..i would try the fstab list when i get home..:)

now isnt there any way on how we could get the fade effect in ubuntu .>i just have an ordinary pc.>ie 1100mhhz.> celerom.>256 mb ram.>i810e motherboard>we do get get the fade effect in kde so why not here???:popcorn:
thanks all,

---

### Post by bronze on 2007-07-12
Can you please define "fade effect". What is it that you want a fade effect on?
Edit: And I find gnome a bit more minimalistic so you're less likely to find fancy effects without customization.

---

### Post by Balvinder25 on 2007-07-12
hi...i believe everyone has used windows xp and windows 2000...when u click on a menu item it fades in and then fades out..this is what i intend to get here is that not possible??

---

### Post by VictorR on 2007-07-12
You may want to install xcompmgr - it can create fade effects and shadows. See this:

[http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527)

read what is said about users with unsupported cards.
You may have to kill xcompmgr in order to logout, I have made this custom launcher for this:
> $ killall xcompmgr

---

