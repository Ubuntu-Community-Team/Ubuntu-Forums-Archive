---
title: "Newb having trouble again"
date: 2009-03-25
forum: General Help
---

### Post by wighttrash on 2009-03-25
Openoffice.org, quanta plus, and amarok are doing something weird.  When i open the programs they will not open all the way and they are unusable.  Not sure what i have done to cause this and a reinstall did not fix it.  Any idea what this problem is and how to fix it.  All of my other programs are working fine (i think).   

Thank you

---

### Post by DGortze380 on 2009-03-25
what do you mean by 'they don't open all the way'?

What are your system specs? Specifically, how much RAM do you have?

---

### Post by Chemical Imbalance on 2009-03-25
post some screenshots please

---

### Post by wighttrash on 2009-03-25
Ubuntu intrepid ibex
2 gigs ram

The programs open but they have no functionality.  It is just a blank screen.  I can't close them or use them.  I can post a screen shot when i get home but it is just a blank screen.

---

### Post by mb_webguy on 2009-03-25
That's not a problem with those applications, but with your window manager and/or video driver.  Try resizing the windows smaller.  You might also want to try either disabling some desktop effects or stop using Compiz entirely.  If you want to keep using Compiz, you should try changing your video driver.  If you have an nVidia card, try installing and running [EnvyNG]("apt:envyng-gtk") (using the command "envyng -t" in the terminal).

---

### Post by wighttrash on 2009-03-25
> That's not a problem with those applications, but with your window manager and/or video driver. Try resizing the windows smaller. You might also want to try either disabling some desktop effects or stop using Compiz entirely. If you want to keep using Compiz, you should try changing your video driver. If you have an nVidia card, try installing and running EnvyNG (using the command "envyng -t" in the terminal).

I did install compiz last night.  I did not think that could have caused the problems.  I will try what you said.  Thank you

---

### Post by wighttrash on 2009-03-25
Using envyng - t to un-install my nvidia driver did the trick.  The programs are working now. Can i still use the desktops effects?  Or are they more hassle then its worth?  Let me know your opinion and thanks for the help.

---

### Post by wighttrash on 2009-03-25
Ok so I re-installed the driver that the envyng -t programs suggests and my programs work just fine but now roughly 1/4 of the right side of my screen is blacked out.  I tried messing with some settings but could not fix it.  Any suggestions?  

Brad

---

