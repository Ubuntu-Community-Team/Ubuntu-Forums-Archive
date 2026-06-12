---
title: "Computer always reboots when shutting down"
date: 2006-01-19
forum: General Help
---

### Post by jazzgossen on 2006-01-19
I have a strange problem: it seems that Ubuntu always wants to restart my computer instead of just shutting it down. 

When I choose shut down from the menu, it shuts down but then immediately powers on again. When I tried to "shutdown now" from the terminal, the shutdown process stopped after a while so that I hade to reboot the hard way.

Any ideas why? Windows and Red Hat never behaved like this on this computer.

---

### Post by darth_vector on 2006-01-19
i think the comand you want is```
shutdown -h now
```

---

### Post by jazzgossen on 2006-01-21
No, that doesn't help. The only difference when running "shutdown -h now" instead of shutting down from the menu is that I get a text-mode login screen while the computer is shutting down instead of seeing the usual shutdown messages. The computer still reboots automatically after it's done shutting down.

---

### Post by jazzgossen on 2006-01-21
Even "showdown -hP now" does the same thing. 

Hmm, strange... almost seems like a hardware issue, only that shutting down from Windows always works.

Any more ideas?

---

### Post by bigken on 2006-01-21
Hi check your bios settings ie power managment settings boot from lan ect see what is enabled. Disable one setting at a time and try it.;)

---

### Post by jazzgossen on 2006-01-23
Problem solved.

Disabling the "power on: any key" helped. That function enabled me to turn the computer on by pressing any key on the keyboard. With that disabled, the computer stays off until I power it on again. I guess that Ubuntu leaves something on the keyboard buffer when shutting down that the BIOS catches.

---

### Post by bigken on 2006-01-25
Ok now you know what it is you could try flashing your MB bios and see if it 
cures the restart problem ;)

---

