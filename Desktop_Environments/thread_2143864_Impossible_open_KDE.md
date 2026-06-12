---
title: "Impossible open KDE"
date: 2013-05-10
forum: Desktop Environments
---

### Post by Paolo5969 on 2013-05-10
Hi, I've a problem after insert username and password on my screen there's this message in a window:
"Kstartup config4 dloes not exist or fails, the error code is 3. check your installation."
click Okay and the KDE load another time username and password, after insert another time reload a window with inside the same message.
Thanks for helping 
Paolo
P.S. I'm Italian and my English isn't good and this is my first thread. Sorry for mistake!

---

### Post by dino99 on 2013-05-10
boot in recovery mode (hit "shift" key down at bios end process to get the grub menu on single OS installation)
activate the network
and select the root console. Then run that command: ```
 dpkg-reconfigure kdm 
```

---

### Post by Paolo5969 on 2013-05-12
After your instructions I had this response:

```
[COLOR=#555555][FONT=Monaco]chow: cambiamento del proprietario di "/var/lib/kdm/kdmsts" :  File system in sola lettura[/FONT][/COLOR]
```

chow: Changing ownership of "/ var / lib / kdm / kdmsts" File system read-only

Can you help me?
Thanks
I've reboot and in a windows there's write:
```
Call to lnusertemp failed (temporary directories full?) Check your installation
```
What's mean?

---

