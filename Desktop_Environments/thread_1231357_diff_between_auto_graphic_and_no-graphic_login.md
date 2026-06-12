---
title: "diff between auto graphic and no-graphic login"
date: 2009-08-04
forum: Desktop Environments
---

### Post by ubu_can on 2009-08-04
Ubuntu 9.04 (64-bit):  Let me explain. I wanted to boot to the console and then if I wanted to run startx. For this, as I read somewhere, I went into the /etc/rc2.init/ and changed the name S30gdm to K30gdm. That did the trick. However:

1)  the (default) graphical login somehow installed a few extra drivers wherein 
   a) the sound worked ok,
   b) if I attached an external USB drive, it would be shown on my desktop
   c) possible some other stuff, still undetected.

2) the manual graphical interface (through startx) apparently did not load the above drivers (?). I can play and hear an mp3, say, from the console, before I run startx (mplayer song.mp3), once I run startx and enter the graphical environment all sounds are off. Moreover, if I attach an external usb drive, I have to manually mount it, through mount ..etc.  The latter is not so bad, as I can edit my fstab file to have them registered, but I have not found any way to make the sound work. (I think I also tried another executable, gdm or something like that) that gave me the login interface again, but still the end was not much different from what I got when I ran startx, that is still no sound).

3) The most troubling thing now is that after I changed the session a couple of times (through the Options menu on the graphical login) I cannot go to the default settings as they are outlined on 1) above. :-( Barring a re-installation of the whole thing, is there any way of controlling all these?

Thanks...

---

