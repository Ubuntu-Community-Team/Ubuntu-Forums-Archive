---
title: "Can't Launch Sudo Apps from Desktop!"
date: 2005-10-18
forum: Desktop Environments
---

### Post by shekhark on 2005-10-18
I am experiencing a problem with launching applications from the GNOME desktop under the Applications and System menus, in which whenever I select an app that requires sudo privileges (such as Synaptic, Root Terminal, or Networking), it will simply not start after selection from the menu. Some apps appear on the bottom window list as 'Starting x...' but then disappear and fail to start. I can of course go to a terminal and launch apps from sudo x... after entering my root password, but for some reason they will not launch from the menus on the desktop at all. I recently changed my user and root passwords, though I presume this has nothing to do with the problem, perhaps it does. I also tried re-installing the gnome-desktop packages, adding a new GNOME menu to the panel, etc. but nothing seems to work. Please help!

---

### Post by migueljacq on 2005-10-18
[QUOTE=shekhar@crit.org.in]I am experiencing a problem with launching applications from the GNOME desktop under the Applications and System menus, in which whenever I select an app that requires sudo privileges (such as Synaptic, Root Terminal, or Networking), it will simply not start after selection from the menu. Some apps appear on the bottom window list as 'Starting x...' but then disappear and fail to start. I can of course go to a terminal and launch apps from sudo x... after entering my root password, but for some reason they will not launch from the menus on the desktop at all. I recently changed my user and root passwords, though I presume this has nothing to do with the problem, perhaps it does. I also tried re-installing the gnome-desktop packages, adding a new GNOME menu to the panel, etc. but nothing seems to work. Please help![/QUOTE]

Someone earlier had a similar problem with the root terminal not opening, they restarted and it worked. Doubt that this would be a likely solution for the problem but worth a shot!
I wonder if any error messages in the system log or /var/log/messages are logged when this sort of thing happens

---

### Post by manicka on 2005-10-18
Does the user you are logged in as, have sudo priviliges

---

### Post by hashimoto on 2005-10-18
[QUOTE=shekhar@crit.org.in]... (such as Synaptic, Root Terminal, or Networking), it will simply not start after selection from the menu...[/QUOTE]

I had the same problem after an expert installation for Breezy. Turned out that my username was not on the sudoers list.

Open terminal, su to root then run visudo. Add your username as a last row and use the same permissions as root on the line above (...ALL(ALL)something). Then CTRL-X (to save and exit, if memory serves). That should do it.

Hope this helps.

---

### Post by shekhark on 2005-10-18
Thanks for your help, I added my username to sudoers, but it has not made any difference to this problem. Any other suggestions?

---

### Post by nobby_trussin on 2005-10-18
yeah mine did exactly the same and it was cured by a reboot. seems to be when you've first installed breezy. this also happens with hoary. 

also the weird thing is, if you look at what command the link performs and perform that command from the terminal it works fine! 

its something odd to do with gksudo but who knows

regards 

nobby

---

### Post by shekhark on 2005-10-18
This has not been cured by any number of reboots! Perhaps this is a bug that needs to be fixed.

---

### Post by hunteramor on 2005-10-18
same problem here, i've rebooted several times and it hasn't magically gone away yet.

---

### Post by hunteramor on 2005-10-18
tried adding my user to sudoers, didn't do anything.

---

### Post by shekhark on 2005-10-18
Is this a bug with gksudo in Breezy? I also seem to be experiencing problems logging in as root from a terminal, with the terminal often hanging. Maybe it's just something peculiar to my system, but perhaps not. 

P.S. 'Try rebooting', while excellent advice, is something I would presume that most people would try doing before posting a problem or bug to these forums. That and 'check Google'.

---

### Post by jackiemcghee on 2005-10-19
I'm bumping this because I've just run into the same problem. Clean install from CD then changed to the 686 kernel, added nvidia, mysql, postgres, php4, phpmyadmin, phppgadmin, ruby, rails. Then I did a couple of updates via the notification area and now synaptic, root terminal, netowrking all fail when launched from the menu.

This is an actual problem.

---

### Post by hunteramor on 2005-10-19
I just tried a complete removal and then reinstallation of gksu and gdm to fix this, and it didn't work.  I still get the "Starting _____..." in the taskbar, and then after a few moments, nothing at all.

---

### Post by shekhark on 2005-10-19
I also tried re-installing gksu and gdm, which didn't solve the problem. Will be sitting with one of the Ubuntu developers (Mako) on this later today, and will send an update on what happens and hopefully also file a bug report.

---

### Post by hunteramor on 2005-10-19
thanks, please post what you find out, it's really been bothering me.

---

