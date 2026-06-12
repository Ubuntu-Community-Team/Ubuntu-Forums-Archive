---
title: "Beryl installed, but won't start"
date: 2007-01-31
forum: Desktop Environments
---

### Post by clothrh on 2007-01-31
I have two systems running Ubuntu, and I've been running Beryl on my older PC with a nVidia card for about 45 days or so, and it has been running flawlessly, with negligible performance drag and no hiccups.  I decided to see how it would run on my newer machine with an ATI card, and installed beryl from the httt://ubunut.beryl-project.org/ edgy main repository.  However when I initiate beryl from the terminal it doesn't start properly.  I don't see the splash screen, but the diamond icon pops up on the tool bar like it is running as usual.  In the diamond's menu drop-down, under 'Select Window Manager,' Metacity is still selected, and when I select it to use Beryl, I get the following output from the terminal:

```
clothrh@RC2:~$ Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension
```

So what's killing X? And what's up with the "beryl: No composite extension"?

Thanks for any help,
Richard

---

### Post by kvonb on 2007-01-31
ATIs can be a real pain in the backend!

Which driver are you using?  For ease of Beryl setup I recommend the opensource (default) driver under Edgy, see my how-to here:

[http://ubuntuforums.org/showthread.php?t=301364](http://ubuntuforums.org/showthread.php?t=301364)

I wrote that with the LiveCD in mind, but it works exactly the same on a standard install, although if you installed any video drivers you will have to undo what you have already done!

---

### Post by avelala on 2007-01-31
i'm having the same problem, Beryl is running in GNOME, but i can't get it to change from Metacity, to Beryl.  this is the warning i get when i run beryl in the terminal

```
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```

any help would be appreciated!!

---

### Post by clothrh on 2007-02-01
Okay, it just got worse.  I tried to restart X, just on a whim to see if it would fix the problem, and now X is freaking out.  It's giving me a flashing, blueish screen that I can't get past.  Any ideas? Should I just replace xorg.conf with the back-up copy?

---

### Post by raul_ on 2007-02-01
Are you using the latest drivers? Have you created a new session for XGL? Remember that Beryl with ATI is not installed the same way that Beryl with NVidia

---

### Post by clothrh on 2007-02-01
Yes, I installed new drivers immediately before progressing with the beryl install, which fixed my screen resolution problem.  I followed the ATI wiki for the driver update, and then followed a wiki for installing beryl, but I can't seem to find the address for it. The process was fairly straight-forward, using the [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main depo.  The direct rendering is turned on, so I'm pretty sure the driver is set up properly, but I don't know for sure. I didn't create a separate session to use beryl, but I didn't think that was necessary unless I wanted beryl to start at boot.

---

### Post by raul_ on 2007-02-01
It's absolutely necessary, otherwise it won't work. try creating a new one, following the guide and then try starting beryk in the xgl session

---

### Post by clothrh on 2007-02-01
Ok, X is stable again, but I still can't select beryl as the window manager.  I completely removed beryl and proceded to try it in a new session, but it still won't work, although the error is different this time:

```
[INDENT][INDENT]**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3400003 specified for 0x3400082 (acroread).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x34001dc specified for 0x34001f6 (Adobe Read).
```


Any ideas? I'm still having the same problem with beryl not able to select itself as the window manager.

On a side note, why does the ATI card require a new session to run beryl?  I didn't have to do that for my nVidia card.

---

### Post by raul_ on 2007-02-01
what happens if you type "emerald --replace" ?

---

### Post by glabouni on 2007-02-01
[http://ubuntuforums.org/showthread.php?t=351319](http://ubuntuforums.org/showthread.php?t=351319)

---

