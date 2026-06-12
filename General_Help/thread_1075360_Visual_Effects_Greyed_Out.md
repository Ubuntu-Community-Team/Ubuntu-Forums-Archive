---
title: "Visual Effects Greyed Out"
date: 2009-02-20
forum: General Help
---

### Post by saraswathula on 2009-02-20
Toshiba Laptop
Compiz-Check
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

All options on System -> Preferences -> Appearance -> Visual Effects are completely greyed out.

I have installed Compiz-Config, but that is also totally disabled. Please help me.

---

### Post by saraswathula on 2009-02-20
I forgot to add the compiz-config screenshot. Here it is. Thanks for your help.

---

### Post by overdrank on 2009-02-20
Hi and welcome, have you tried running compiz from the terminal or using the alt F2 keys?
```
compiz --replace
```
Another thing you may look at is the amount of memory in the system as it is shared with the intel graphics.

---

### Post by saraswathula on 2009-02-20
Overdrank,

Thanks a lot for the reply.

I just ran the command "compiz --replace". That enabled the options in Visual Effects. But when I select any option - Normal, Extra or Custom - the screen blink a few time, and then returns with the message "Desktop effects could not be enabled". 

The selection on the Visual Effects tab returns to 'None'.

Anything else that could be done?

The system has a total of 2GB RAM.

Regards,

---

### Post by overdrank on 2009-02-20
> **saraswathula said:**
> Overdrank,

Thanks a lot for the reply.

I just ran the command "compiz --replace". That enabled the options in Visual Effects. But when I select any option - Normal, Extra or Custom - the screen blink a few time, and then returns with the message "Desktop effects could not be enabled". 

The selection on the Visual Effects tab returns to 'None'.

Anything else that could be done?

The system has a total of 2GB RAM.

Regards,

Could you use that command in the terminal and post the output. Because that command should enable the effects without changing any settings on the visual effects tab.
Also when you ran the compiz-check was there any other output like pertaining to the resolution?

---

### Post by saraswathula on 2009-02-20
> **overdrank said:**
> Could you use that command in the terminal and post the output. Because that command should enable the effects without changing any settings on the visual effects tab.
Also when you ran the compiz-check was there any other output like pertaining to the resolution?

When I ran that, it hangs midway, at the point where it says 'Cant find compiz-real'. I have to hit ^C, and then the whole GUI crashes. None of the other active applications are responsive. The CPU is however only 2% utilization.

I have to restart the system. Maybe there is something wrong with the installation of Compiz, or the graphics driver. I would appreciate if you could let me know what could be done? Maybe uninstall Compiz completely (how do I do that?), and then reinstall. Please note that compiz-check works fine through all this, and there is nothing pertaining to resolution or anything else. Everything is fine there.

Thanks a lot, and regards, SS

---

### Post by phoenixrising186 on 2011-04-07
I had the same problem, but then I enabled the compiz thing and I could change the visual effects, but everytime I close the appearence window it goes back to none?

Any idea why?

---

