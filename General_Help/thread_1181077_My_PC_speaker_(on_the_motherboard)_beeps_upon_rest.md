---
title: "My PC speaker (on the motherboard) beeps upon restart or shutdown"
date: 2009-06-07
forum: General Help
---

### Post by diablo75 on 2009-06-07
I am running Ubuntu 9.04, fresh install (well a fresh root partition, the home folder is leftover from a previous install).

Every time I shut my computer down or restart, I hear several very rapid beeps (practically one beep but it's really several that happen very very fast).  I never see any errors appear when this happens or after so I don't know what to make out of this.  Is there a log file perhaps that could shed some light on this?

---

### Post by talonstriker on 2009-06-07
I have the same problem.  As a workaround, I typically log off, then shutdown from the login screen.  This does the job, but I hope to find a better solution soon.

---

### Post by Idaho Dan on 2009-06-07
Mine does the same thing after installing 9.04.
It never did it before.

---

### Post by nacho32 on 2009-06-07
this is really nothing to worry about, you should be able to disable it in the bios

---

### Post by hyperdude111 on 2009-06-07
This is called system-beep, it is not an error but is a feature of ubuntu.

Go System-preferences-sound

System beep tab - Disable system beep. 

This guide was the source of my info [http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/](http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/)

---

### Post by talonstriker on 2009-06-07
> **hyperdude111 said:**
> This is called system-beep, it is not an error but is a feature of ubuntu.

Go System-preferences-sound

System beep tab - Disable system beep. 

This guide was the source of my info [http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/](http://www.foogazi.com/2008/05/01/how-to-disable-the-system-beep-in-ubuntu/)

This turns off all the system beeps except for the shutdown beep.

---

### Post by michy99 on 2009-06-07
Edit the file /etc/rc.local```
gksu gedit /etc/rc.local
```and make it look like```
#!/bin/sh -e
# ...
for console in /dev/tty[1-7]; do 
    setterm -blength 0 >$console
done
exit 0
```Make it executable with```
sudo chmod +x /etc/rc.local
```Then after rebooting once the shutdown beep should be gone.

---

### Post by diablo75 on 2009-06-07
Well if it's supposed to happen I think I'll just leave it alone.  I was worried that it might be indicating some sort of error behind the scenes...

---

### Post by Forneus on 2009-06-25
> **michy99 said:**
> Edit the file /etc/rc.local```
gksu gedit /etc/rc.local
```and make it look like```
#!/bin/sh -e
# ...
for console in /dev/tty[1-7]; do 
    setterm -blength 0 >$console
done
exit 0
```Make it executable with```
sudo chmod +x /etc/rc.local
```Then after rebooting once the shutdown beep should be gone.


Beautiful, worked like a charm :D

---

