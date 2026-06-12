---
title: "Remnants of the Precursors"
date: 2022-02-20
forum: Gaming &amp; Leisure
---

### Post by demonenero84 on 2022-02-20
I installed Remnants of the Precursors, when I try to run it in a terminal I use this command :

[FONT=monospace][COLOR=#000000]/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=Remnants.sh com.remnantsoftheprecursors.ROTP

and I get this message:

maxMB:7891  freeMB:4419  allocMb:1974   bits:64
restarting with MB:2630
Only 1974Mb memory allocated by OS. Restarting game with command: java -Xmx2630m -jar Remnants.jar arg1

Any suggestions?
thanks a lot in advance
[/COLOR]


[/FONT]

---

### Post by Dennis N on 2022-02-20
On Ubuntu 20.04 (Gnome desktop), it starts and run without a problem. Unless there is some special reason, you shouldn't need to start this from the terminal. The Flatpak installation creates an entry in the Application menu. Try using that to start it. Screenshot attached.

---

### Post by demonenero84 on 2022-02-20
thanks a lot for the reply
So if I start the game using the application menu nothing happens, I tried running it on a terminal to see the kind of error I get.
As a matter of fact I downloaded the file "Remnants.jar" and that version of the games runs fine, I decided to install it using flatpak so the game updates
thanks

---

### Post by demonenero84 on 2022-02-22
So I posted in the official reddit 
[https://www.reddit.com/r/rotp/comments/sxx9bz/remnants_of_the_precursors_ubuntu_installation/](https://www.reddit.com/r/rotp/comments/sxx9bz/remnants_of_the_precursors_ubuntu_installation/)
this problem has been fixed, just update your flatpak

---

