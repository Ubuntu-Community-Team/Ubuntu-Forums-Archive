---
title: "e17 &quot;Enlightenment error: This is very bad.&quot;"
date: 2012-05-13
forum: Desktop Environments
---

### Post by sirriffsalot on 2012-05-13
Hi!

Since most of the other desktop environments I've come across aren't what I'm after, I finally found e17 which seems to serve my needs well... But there is a curse upon me it seems, because now, with a fresh 12.04 Ubuntu install, whenever I simply click on the desktop and navigate to "Applications > Accessories" with my mouse, I get the title error... It goes as follows:

```
Enlightenment error: This is very bad. Enlightenment SEGV'd.
This is not meant to happen and is likely a sign of a bug in Enlightenment or the libraries it relies on. You can gdb attach this process now to try to debug it, or you could exit, or you could just restart to try and get your desktop back the way it was. Please compile everything with -g in your CFLAGS.
```

Any ideas on this one...? Appreciate your time!

--> Leo

---

### Post by kevinmchapman on 2012-05-13
Bit of a guess, this, but E17 assumes that xterm (basic terminal emulator) is installed, and puts an entry in the Applications > Accessories menu, so I wonder if the problem is with the .desktop item for xterm.

Try installing xterm and see if that serves as a workaround. Alternatively, check if there is an xterm.desktop item in /usr/share/applications, and delete it if there is. If that exists without xterm being installed, it would cause issues.

---

### Post by sirriffsalot on 2012-05-13
Thanks for responding!

I'm afraid the problems are more severe, and I've already reinstalled once... The more I use e17, the more this problem arises... Scrolling up and down a filemanager too quickly or moving a volume control sets this error message off at seemingly times (sometimes it work, but mostly it ends up with an error message). I'm really getting tired of being the most unlucky person to have crossed the linux world... I spent one month just getting my computer setup correctly for studio purposes... Haha:)

--> Leo

---

### Post by Frogs Hair on 2012-05-13
One option is to login to Ubuntu and open hidden folders in nautilus and delete .e folder . The next time you login to E17 it will be a brand new configuration and you will have to set everything up again. 

I used the PPA at the link on 11.10 and it is far more up to date and allows for more user options than the old core packages from the repository.

You will have to remove the .e folder and all the other E17 prior to installation.        

[http://ubuntuguide.net/install-enlightenment-e17-in-ubuntu-12-04-previous-via-ppa](http://ubuntuguide.net/install-enlightenment-e17-in-ubuntu-12-04-previous-via-ppa)

---

### Post by Frogs Hair on 2012-05-13
I installed the above PPA 0n 12.04 and it's running great.

---

### Post by Tux Aubrey on 2012-05-14
> **Frogs Hair said:**
> I installed the above PPA 0n 12.04 and it's running great.

Same here.  After a false start with 12.04, everything is now working fine for me and e17 is very stable on both 11.10 and 12.04 (I have both 32 and 64 bit setups on different machines and they are rock solid - as well as being speedy, beautiful and efficient).  I haven't seen the good ole "This is very bad" error for a long time now. :)

Take Frog Hair's advice and completely uninstall your existing e17 and all components, not forgetting the hidden .e directory in your home folder.  Then add the hannes-janetzek ppa and do a fresh install (I'd suggest using synaptic and adding e17 and the modules you want from there).

---

### Post by sirriffsalot on 2012-05-14
I'll try compiling from source I suppose, thanks for helping me out and hope this helps someone else!

---

### Post by Fred999 on 2013-04-27
Ah, the old "Enlightenment Segv'd.  This is very bad." message.  Looks rather daunting.  I panicked the first time I saw it, for sure.  The best fix is indeed to get a better copy from the right source (and now there is a stable version!  -After only 12 years or so of development!)  

Still, if you get that message, E17 has a lovely feature.  Simply take a deep breath, and press F1, once only.  Your screen should go black for a few distressing moments, and then generally speaking, you get your system restored to where it was before the Seg fault occurred.   Sometimes I have lost only the last thing I was doing, but the rest of my work comes up, the desktop intact, and whatever I was doing 10 minutes before is untouched.  Beats shutting it down when you don't know about that trick.  Anyway, cheers!

---

