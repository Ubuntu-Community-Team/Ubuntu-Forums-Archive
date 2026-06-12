---
title: "[SOLVED] unable to start ubuntu"
date: 2009-01-05
forum: General Help
---

### Post by atinsood on 2009-01-05
i was trying out some new themes on ubuntu yesterday and installed a few new programs(global menu bar). But now on restarting no login screen shows up and the pc freezes with a blank screen instead of logging in screen. I tried the recovery mode also but same case there also. I am using Ubuntu Intrepid Ibex. Also there is no option of boot the last best known config.

---

### Post by atinsood on 2009-01-07
> **atinsood said:**
> i was trying out some new themes on ubuntu yesterday and installed a few new programs(global menu bar). But now on restarting no login screen shows up and the pc freezes with a blank screen instead of logging in screen. I tried the recovery mode also but same case there also. I am using Ubuntu Intrepid Ibex. Also there is no option of boot the last best known config.

I am not why no one is replying to this.. is my question too vague or does it make no sense at all.. Please please let me know in case you need me to rephrase the question or provide additional details

---

### Post by cariboo on 2009-01-07
I would suggest starting in recovery mode, and select xfix at the menu, when it is done coose resume and see if you can get back to your desktop. xfix creates a new etc/X11/xorg.conf file, so you may have to reload the restricted drivers. 

If the above doesn't work, try removing the package you installed, at the prompt type:

```
apt-get purge <packagename>
```

then run:

```
apt-get autoremove
```

the above command will remove any leftover dependencies that didn't get removed using the purge command. It will also remove any archived packages in /var/cache/apt/archives.

Jim

---

### Post by namdung on 2009-01-07
In the Login menu select *Options==>Select Session==>Failsafe GNOME*. If you are able to login then remove the particular theme causing the issue.

---

### Post by atinsood on 2009-01-07
> **cariboo907 said:**
> I would suggest starting in recovery mode, and select xfix at the menu, when it is done coose resume and see if you can get back to your desktop. xfix creates a new etc/X11/xorg.conf file, so you may have to reload the restricted drivers. 

If the above doesn't work, try removing the package you installed, at the prompt type:

```
apt-get purge <packagename>
```

then run:

```
apt-get autoremove
```

the above command will remove any leftover dependencies that didn't get removed using the purge command. It will also remove any archived packages in /var/cache/apt/archives.

Jim

Jim

Even if i start it in recovery mode the screen freezes after some time and nothing shows up. I think the only way for me to fix it will be via command mode... but m not sure how to do this.

---

### Post by atinsood on 2009-01-07
> **namdung said:**
> In the Login menu select *Options==>Select Session==>Failsafe GNOME*. If you are able to login then remove the particular theme causing the issue.

The problem is I am never getting thr login screen. Ubuntu freezes with a blank screen when it is supsd to show me the login screen

---

### Post by stanca on 2009-01-07
I think you can access the command line from grub?

---

### Post by atinsood on 2009-01-07
> **atinsood said:**
> Jim

Even if i start it in recovery mode the screen freezes after some time and nothing shows up. I think the only way for me to fix it will be via command mode... but m not sure how to do this.

Jim

I was actually able to fix it via the recivery mode by using xfix.. 
thx a ton...

---

