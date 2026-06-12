---
title: "How to install NVIDIA Graphix"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Prudentissimus on 2005-06-22
Hello,


 When I want to install the GFX Driver for NVIDIA... It says I have to quit X-Server or something... How do I do it?

-Thanks

---

### Post by pdpi on 2005-06-22
[QUOTE=Prudentissimus]Hello,


 When I want to install the GFX Driver for NVIDIA... It says I have to quit X-Server or something... How do I do it?

-Thanks[/QUOTE]
 just log out and press ctrl+alt+backspace. Or restart the system. The X Server is the program that does the workhorse stuff for the graphical environment. Both Gnome (Ubuntu) and KDE (Kubuntu) run atop of it.

---

### Post by frodon on 2005-06-22
try that [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installnvidiadriver](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installnvidiadriver)

---

### Post by Prudentissimus on 2005-06-22
[QUOTE=frodon]try that [http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installnvidiadriver](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#installnvidiadriver)[/QUOTE]
 I dun have Internet access on the linux box... but I do have a *.run file I downloaded from NVIDIA's website...

So How do i do it??? When I do CTRL+ALT+Backspace, it just reboots into the login screen...

---

### Post by frodon on 2005-06-22
[QUOTE=Prudentissimus]I dun have Internet access on the linux box... but I do have a *.run file I downloaded from NVIDIA's website...

So How do i do it??? When I do CTRL+ALT+Backspace, it just reboots into the login screen...[/QUOTE]

you really don't have internet connection on your computer ! 
because if you have it's easier for newbie to do it via apt-get. If not after CTRL+ALT+Backspace, do CTRL+ALT+F1 enter your login and go to the repertory where you download your .run fiie and and launch it, I hope the installer will not see active Xserver.

---

### Post by cutOff on 2005-06-22
You can have a look to

[http://ubuntuforums.org/showthread.php?t=39743&highlight=NVIDIA](http://ubuntuforums.org/showthread.php?t=39743&highlight=NVIDIA)

---

### Post by pdpi on 2005-06-22
Sorry, when you said quit I read restart, since I didn't need to actually quit X to install the drivers. Unfortunately, just going to Ctrl+Alt+F1 for a terminal won't suffice, as the X server will still be open.

The easiest way to do this should be downloading the .deb file for ubuntu from your local repository and installing it with dpkg. That's 

```
dpkg -i nvidia-installer-thingy.deb
```

If I'm not mistaken (I don't do many dpkg installations)

---

