---
title: "freezes at bootscreen with xgl"
date: 2006-06-30
forum: Desktop Environments
---

### Post by dicaguido on 2006-06-30
Hello!
New problem: i installed xgl; after i restarted the laptop before the bootscreen it goes black for a few times (alternating with random color screen) before goin' black....forever.... #-o 
I think it's xgl; my question is how can i return to xorg as a graphical mode?
I can't access the os so the only chance is the command line in recovery mode. It's just that i don't know the commands......... :( 
And is there any way to rescue the system to the original configuration without reinstalling it (i tried with the recue option in the cd but it seems it needs to access the graphical system).
Thx

Sorry, ubuntu freezes before the login screen

---

### Post by dicaguido on 2006-06-30
I forgot to say that maybe i installed with the wrong procedure..... 
xgl from synaptics and command to switch from xorg to xgl...
I want to turn back to xorg!

---

### Post by dicaguido on 2006-06-30
Resolved.
I didn't notice my graphic card was not compatible:
recovery mode
startx (it switches xgl and logs you in graphical mode as root)
search gdm.conf
under "servers" modified 0=xgl with 0=xorg (everytime xgl--> xorg)
restarted and voilà!

---

