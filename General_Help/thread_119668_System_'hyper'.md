---
title: "System 'hyper'"
date: 2006-01-20
forum: General Help
---

### Post by foulplay on 2006-01-20
As I start the system, 1.5gb of ram is used instantly, everything is running EXTREMELY fast, such as the animations, I had to set the keyboard repeat rate all the way up just to keep it from typing 2-5 letters at a time. This is a fresh install of Kubuntu 5.10 (x86, on a AMD64 machine, but AMD64 doesn't support many things I need, such as Flash). I'm just concerned that this could be bad for my system, and that it will hurt my performance.

Edit: it's quickly increasing, it goes up about 100mb of ram per minute once booted....after 3 minutes it's to almost my full 2gb.

---

### Post by thagame on 2006-01-20
no clue on that, but i have a amd64 system and im running java and flash

---

### Post by zachariah on 2006-01-20
The RAM usage is normal - Linux will use as much of your memory as possible, but not in the bad Microsoft way. 

[(See this article)]("http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/")

Don't know about the speedyness...sounds like you might have to use the 64bit version.

---

### Post by shakin on 2006-01-20
[QUOTE=zachariah]The RAM usage is normal - Linux will use as much of your memory as possible, but not in the bad Microsoft way. 

[(See this article)]("http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/")

Don't know about the speedyness...sounds like you might have to use the 64bit version.[/QUOTE]

I'm not sure this much RAM usage is normal. A reasonably default system can't possibly use 2GB.

I would reboot, then immediately load the system monitor and watch which processes are using RAM quickly. With any luck you'll find one that is out of control that you can uninstall or reinstall. At the very least, kill that process right away so you can start using your computer.

I wouldn't even deal with the speed issue until the runaway process problem is fixed. They might be related.

---

### Post by foulplay on 2006-01-20
[QUOTE=thagame]no clue on that, but i have a amd64 system and im running java and flash[/QUOTE]
:confused: I downloaded the installer from macromedia's site, and it said it didn't support the amd64 version of linux.  Maybe it would work if I used firefox?

---

