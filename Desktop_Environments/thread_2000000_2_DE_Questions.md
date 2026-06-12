---
title: "2 DE Questions"
date: 2012-06-08
forum: Desktop Environments
---

### Post by ..jeff.. on 2012-06-08
Hi :)

I used to use Linux, switched to Windows for a while, now I'm looking to go back. A lot has changed since then, which leads to my questions:

1. I'm a heavy user and multitasker. I have a lot of programs open at once, usually multiple instances of programs (browsers, chat, command lines). I see a lot of DEs, such as Gnome Shell, Unity, KDE, etc... Are any of them more heavy user friendly than others?

2. I'm very strict about keeping my PC clean. I uninstall programs I don't use often, keep the number of processes / services to a minimum, clean the Windows registry often, etc... Does installing multiple DEs have any negative side effects in that sense?


Thanks for your help!

---

### Post by dniMretsaM on 2012-06-08
> **..jeff.. said:**
> 1. I'm a heavy user and multitasker. I have a lot of programs open at once, usually multiple instances of programs (browsers, chat, command lines). I see a lot of DEs, such as Gnome Shell, Unity, KDE, etc... Are any of them more heavy user friendly than others?

It just depends on how you work. I recommend trying some live USB's out and seeing which you prefer.

> **..jeff.. said:**
> 2. I'm very strict about keeping my PC clean. I uninstall programs I don't use often, keep the number of processes / services to a minimum, clean the Windows registry often, etc... Does installing multiple DEs have any negative side effects in that sense?


Thanks for your help!

The more DE's you install, the more libraries and programs you will need to install (i.e. GNOME requires the GNOME and GTK libraries, KDE uses KDE and Qt libraries, GNOME uses Gedit, KDE uses Kate, LKDE uses Leafpad, etc. etc.).

---

### Post by 3Miro on 2012-06-08
> **..jeff.. said:**
> Hi :)

I used to use Linux, switched to Windows for a while, now I'm looking to go back. A lot has changed since then, which leads to my questions:

1. I'm a heavy user and multitasker. I have a lot of programs open at once, usually multiple instances of programs (browsers, chat, command lines). I see a lot of DEs, such as Gnome Shell, Unity, KDE, etc... Are any of them more heavy user friendly than others?

It all depends on the user, some people like some environments better, others like others. The only way to be sure on what you would like is to install them all and try them all.

> 
2. I'm very strict about keeping my PC clean. I uninstall programs I don't use often, keep the number of processes / services to a minimum, clean the Windows registry often, etc... Does installing multiple DEs have any negative side effects in that sense?


There is no Linux registry that can get corrupt and affect the entire system. Linux only loads what you need in memory, any programs that are installed and not running, simply take space on the HDD and do not affect other programs. Speaking of HDD, you can easily have Unity, Gnome-shell, KDE, XFCE and LXDE installed on under 20GB of HDD space. You can also easily uninstall something should you decide that you don't want it anymore.

Check here on how to install and uninstall the various DE:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by ..jeff.. on 2012-06-08
Thanks guys. Aside from the 3 I mentioned (Gnome Shell, Unity, and KDE), any other DEs I should look at, or are those the best ones?

For the clean system, when you uninstall a package, does it remove anything dependent on it that won't be used anymore? I'm more worried about residual things being left behind. Maybe I'm too used to looking at msconfig / windows services and seeing 10000000 startup programs and services that I'm jaded....

---

### Post by raptir on 2012-06-08
> **..jeff.. said:**
> Thanks guys. Aside from the 3 I mentioned (Gnome Shell, Unity, and KDE), any other DEs I should look at, or are those the best ones?

The three you listed are good places to start. As far as I know there is no live CD of gnome-shell with Ubuntu, but you could check out the Fedora 17 live disc to get a taste of the interface. You mentioned that you like to run a lot of programs at once, and those three will all give you good ways to switch between them. I personally found that KDE was a little too "busy" with the effects, like transparency and blur, and that it could make it a bit distracting when running a lot of programs. Xfce and LXDE are the other two major desktop environments, and both offer a simpler interface with less flash. 

> **..jeff.. said:**
> For the clean system, when you uninstall a package, does it remove anything dependent on it that won't be used anymore? I'm more worried about residual things being left behind. Maybe I'm too used to looking at msconfig / windows services and seeing 10000000 startup programs and services that I'm jaded....

It does not remove them automatically, but you can run *sudo apt-get autoremove* to try to scan and automatically uninstall any packages that are no longer needed.

---

### Post by zombifier25 on 2012-06-08
When you remove a package usually everything associated with it will be removed, except for configurations (which can be removed by using the purge option. And again, leaving it sitting on the hard drive is harmless) and dependencies (which can be removed with autoremove)

---

### Post by lolpenguin on 2012-06-09
> **3Miro said:**
> It all depends on the user, some people like some environments better, others like others. The only way to be sure on what you would like is to install them all and try them all.



There is no Linux registry that can get corrupt and affect the entire system. Linux only loads what you need in memory, any programs that are installed and not running, simply take space on the HDD and do not affect other programs. Speaking of HDD, you can easily have Unity, Gnome-shell, KDE, XFCE and LXDE installed on under 20GB of HDD space. You can also easily uninstall something should you decide that you don't want it anymore.

Check here on how to install and uninstall the various DE:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

I got all the full DEs in under 8GiB. (*ubuntu-desktop package). Unlike Windows, where settings usually end up in the registry some way or another, some applications use shared configuration databases, such as GConf (being dumped) and DConf in GNOME, and others keep their own settings.

---

### Post by coldraven on 2012-06-09
I think that a lot depends on your graphics card. If it is a recent one and can run a proprietary driver then everything will be fine.
For example this laptop has an ATI X1250 card an has to use the open source driver. It  has problems with 3D (slow) and can have unexpected faults on some DEs. 
I'm running Cinnamon at the moment, it has some glitches but runs OK and has a modern look.
Experiment with Live CDs until you are happy

---

### Post by 3Miro on 2012-06-09
- If you add/remove programs and you want to clean the dependencies, you can go into the terminal and type:
```
sudo apt-get autoremove
```
this will clean any packages that have been installed as dependencies. There may be another way to do this, but "autoremove" every now and then should be simple enough.

- My favorite environment is XFCE, so I definitely recommend it. Also, I know people that just love the speed of LXDE. Both XFCE and LXDE are relatively small, so it should be easy enough to install/remove.

- When programs get removed, sometimes they will leave configuration files, but those are just small text files of a few kilobytes. Unless you are incredibly restricted on the HDD space (i.e. have 5GB or less), it should make no difference.

- Someone mentioned Gconf or Dconf. There is also the apt database of installed packages, those are similar to the windows registry, but they are not the same. G/Dconf takes care of several Gnome applications, which means that it never get large. For example, no KDE application ever adds anything to GConf, hence installing KDE will not affect Gnome. 

- The APT database will get large and slow as you install more programs, but this will affect only the process of installing and removing programs. APT does not affect the speed of individual programs, it will only mean that every time you hit add/remove/update, you will have to wait a few extra seconds (depending on the speed of your machine).

---

