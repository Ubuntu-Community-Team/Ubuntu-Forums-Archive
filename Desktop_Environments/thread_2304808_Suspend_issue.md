---
title: "Suspend issue"
date: 2015-11-30
forum: Desktop Environments
---

### Post by franlavof on 2015-11-30
Hi guys. I have an Acer laptop with a GeForce 9300m and Kubuntu 14.04 installed. On resuming from suspend mode the kde interface are full of glithces and not usable. I notice that if I plug another screen (via hdmi cable for example) glitch vanish and the interface is again usable. If I return to the laptop screen, KDE is still working fine. So can I automate this, with a script or a keyboard shortcut in order to solve the problem also when I haven't another screen to switch to? How do I do it?

---

### Post by scoutchorton on 2015-12-01
Now, let me just let ya know, I have Ubuntu, so this may not work.

But, you can make Terminal scripts if you save it as a .sh and another command. If you make an empty file and make it something like 'reload.sh', then go to Terminal and do ```
chmod +x [file directory/filename.sh]
```, you just have to double click it to run it. Normally, when you have a file like that, the computer looks at it like a normal text file, so you need the chmod to give it executable permissions (get it, x, eXecutable, Ubuntu distros make so much sense).

In the text file, you would need to put in the command ```
[COLOR=#2E3436][FONT=Open Sans]sudo restart lightdm[/FONT][/COLOR]
``` to restart KDE. If I am thinking right, this should reload the code for the desktop and get rid of your problems.

Anyways, good luck! :D

---

