---
title: "After running nautilus as root, strange rights-problem"
date: 2010-10-18
forum: Desktop Environments
---

### Post by night-wing on 2010-10-18
Hi.

In maverick, I made a menu shortcut to be able to run nautilus as root (gksu nautilus), when I need to (for example, to clean the /var/apt/archives or anything like that).
When I used this in intrepid, karmic or lucid, this worked fine.

In maverick, when I do so, I always afterwards have the gnome desktop of root and still the rights of root outside nautilus. I have to logoff and re-login as my user to see my personal background and gnome environment again.

Can someone give me a hint, how to fix this bug?

Regards
nightwing

---

### Post by mister_playboy on 2010-10-18
I noticed there is a key icon in the notification area that mentions "drop all elevated privileges".  Does that display as root?  What happens if you use it?

---

### Post by night-wing on 2010-10-19
Where did you notice this icon? I did never notice such a key?

---

### Post by ankspo71 on 2010-10-19
Hi, 
I'm not having the same problem so I don't know if this will work, but try making a shortcut with one of these commands to see if it helps:
```
gksudo nautilus & exit
gksudo "nautilus --no-desktop" 
gksudo "nautilus --no-desktop" & exit
```
They all launch nautilus on my Ubuntu as gksudo. The "--no-desktop" option is there to help prevent root's nautilus from displaying root's desktop. Exit is there to tell gksudo to exit when the command is completed. (exit is what I use when I want to exit sudo -s in the terminal like this):
```
[COLOR="Teal"]james@Ubuntu[/COLOR]:~$ sudo -s
[COLOR="Red"]root@Ubuntu[/COLOR]:~# exit
exit
[COLOR="Teal"]james@Ubuntu[/COLOR]:~$

```

If you are looking for an easy way to free up some space, you can install bleachbit, a nice system cleaner that also cleans away those downloaded deb packages in /var/apt/archives. It is in Synaptic or Software Center. Here's the list of cleaning features: [http://bleachbit.sourceforge.net/features](http://bleachbit.sourceforge.net/features). Last month after I upgraded Lucid to Maverick, I saw it remove roughly 3gb of unneeded clutter. Normally after a fresh install of Ubuntu I see it clean about 1gb.

Hope this helps.

---

### Post by night-wing on 2010-10-19
gksudo "nautilus --no-desktop" 

That helped!
Thank you very much!

---

