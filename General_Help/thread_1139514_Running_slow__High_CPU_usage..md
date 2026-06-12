---
title: "Running slow / High CPU usage."
date: 2009-04-27
forum: General Help
---

### Post by bluewish on 2009-04-27
Hello.

I have Ubuntu 8.04 (Hardy heron), with the Kubuntu desktop on it, so I'm not too sure what you'd class it as.

Whenever I run a program, such as Flash Player in a website, my CPU usage goes between 96% - 100%, and it stays that way until I reboot (though sometimes it stays that way 5 - 10mins and fixes itself), even if I close it.

Also, when running Flash Player (macromedia), it runs extremely slow.

Plus the system runs a tad slow even if I don't run an application like that. The CPU meter jumps up and down, like when I just open an application it usually goes to about 85% usage.

Does anyone know what may be causing this?

---

### Post by kerry_s on 2009-04-27
what are your spec's?
what browser are you using flash in?

kubuntu is kde, the heaviest of the 4 desktops.

---

### Post by bluewish on 2009-04-27
My PC specs:
Intel Celeron D 2.6ghz (256KB cache).
1GB DDR-400 RAM.
ATi Radeon 9550 256mb.


The browser I'm using for Flash is FireFox.

---

### Post by cwbar_1 on 2009-04-27
Open a terminal and type the command "top"  (without quotes)
This should show the processes that are running.  Look for the one that is using the most CPU usage and memory. (press q to stop top)  Post the results for the offending program, and someone should be able to help. Hint: if you open your programs while "top" is running, it will show you all the details

---

### Post by bluewish on 2009-04-28
8241 dan       20   0  382m 159m  32m R 79.5 15.7   1:30.62 firefox
 4935 root      20   0  221m  65m  10m R  7.3  6.5   4:36.95 Xorg

---

### Post by mysoogal on 2009-05-16
if your having issues playing flash video in youtube check out this post i made, [http://ubuntuforums.org/showthread.php?t=1120401&highlight=flash+player+slow](http://ubuntuforums.org/showthread.php?t=1120401&highlight=flash+player+slow)

im sure it will fix your problems :D

---

### Post by Tipped OuT on 2009-05-16
> **bluewish said:**
> My PC specs:
Intel Celeron D 2.6ghz (256KB cache).
1GB DDR-400 RAM.
ATi Radeon 9550 256mb.


The browser I'm using for Flash is FireFox.

Can I have your graphics card please!!? I have an ATI Radeon 9100 128 MB's...trade? :D

---

