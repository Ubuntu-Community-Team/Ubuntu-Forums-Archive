---
title: "Help installing KDE"
date: 2009-04-12
forum: General Help
---

### Post by AlbHeart on 2009-04-12
Hello guys,

Being relatively new to Ubuntu, I encountered a problem and dropped by to ask some help. 

I tried to install KDE in Ubuntu using:

> sudo apt-get install Kubuntu-desktop

and that's what I got:

> admin@admin-desktop:~$ sudo apt-get install kubuntu-desktop
sudo: timestamp too far in the future: Apr 12 14:12:18 2009
admin@admin-desktop:~$ 


Any help would be appreciated.

Thanx in advance.

---

### Post by coffeecat on 2009-04-12
I've seen this 'timestamp too far in the future' error during first bootup after a fresh install of a previous release of Ubuntu - can't remember which one. I think there was a minor bug in the installer that got confused between the variations permutations and combinations of GMT, UK summer time and how your system clock was set. It sorted itself out when I let an hour elapse. :p

I didn't realise it affected apt-get and stopped apt-get from working. That's interesting. Suggest you check the settings in the clock applet and adjust if necessary, and reboot. And if that doesn't work, leave it for more than an hour before trying again.

And if that doesn't work, I'm sorry but I haven't a clue.

---

