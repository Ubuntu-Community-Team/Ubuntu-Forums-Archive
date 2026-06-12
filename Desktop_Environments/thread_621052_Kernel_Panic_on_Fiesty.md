---
title: "Kernel Panic on Fiesty"
date: 2007-11-23
forum: Desktop Environments
---

### Post by jflowers on 2007-11-23
I have been running my Dell XPS 410 which had ubuntu pre-installed for the past three months with no problems.  Recently, I added a new path to my /etc/environment file for a program I am using.  After adding this the system still worked fine for a day.  Then one time I restarted my system and the computer stalled during shutdown.  While I was away, somebody else hit the power button to just turn off the machine.  Ever since, I have been having troubles booting.  Initially, during startup, the grub would appear to load but then it stalled with "starting up" on the screen.  Following another power down, the system after starting grub would then output a series of warning with "kernel panic - not syncing attempting to kill".  Another restart actually brought up the ubuntu loggin screen, but neither the mouse or keyboard is active.  I am very new to the linux game, so any help would be greatly appreciated. 

Thanks!

---

### Post by jflowers on 2007-11-23
I am not sure why this worked, but after shutting down my computer, I unplugged everything from the CPU, opened up the side of the computer, pushed in all connections (although none were loose), replugged in everything, and restarted.  From then on, it all worked.  I assume it had something more to do with me completely disconnecting the power, but I really don't have a clue.  Nonetheless, if you ever have a problem with booting your computer after a failed shutdown, try unplugging it first.

---

### Post by Crakie on 2007-11-23
You will have to provide more information on how to debug is this problem. May I suggest you boot to Grub, select the line you usually use to start Ubuntu and use 'e' to edit the boot parameters. You will probably find 'quiet splash' in the kernel line. Remove these and press 'b' to boot. You will now get verbose output, which will give some insight in what is going wrong. Usually the last lines before the panic provide the info required. You can post them here for people to take a look at.

---

