---
title: "Changing Desktop behaviour in Ubuntu 11.10"
date: 2011-10-26
forum: Desktop Environments
---

### Post by lads on 2011-10-26
Hello everyone, I'd like to know how to these two things in Ubuntu 11.10:
[LIST]
[*]Increase the number of Desktops from 2 to 4;
[*]Disable the auto maximize window option.
[/LIST]

I'm used to have the four desktops, 2 south-north and 2 east-west, but after upgrading to Ubuntu 11.10 it reduced to just 1 south-north. I've changed the number of [Vertical and Horizontal desktops at CompizConfig]("http://ubuntuforums.org/showthread.php?t=1723321"), but to no effect.

It took me quite some time to understand why some windows would auto-maximize when I switched desktops, not a bug just an annoying new feature. I changed the [Automaximize value]("http://www.ubuntuvibes.com/2011/06/ubuntu-1110-updates-new-window-auto.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+UbuntuVibes+%28Ubuntu+Vibes%29") to the maximum, also to no effect.

I'd appreciate any info on how to accomplish these two things. Thanks.

---

### Post by ajgreeny on 2011-10-26
I think that automaximise is part of the **grid** plugin of compiz.  Try disabling that and see if it helps.  This is all from memory as I am not running 11.10, but I did take a long look at it and quickly decided not was not for me.

---

### Post by JRV on 2011-10-26
My installation defaulted to four desktops, so I can't help with that problem.

To disable the automaximize:

Open a terminal and enter this code:
```

sudo apt-get install compizconfig-settings-manager
ccsm

```
Near the bottom of the page, uncheck "Grid"

Then open the Ubuntu Unity Plugin under the Desktop heading.

Click on "Experimental" and change the "Automaximize Value" to 100%.
___

---

### Post by lads on 2011-10-26
Thank you for the replies. I had already set the "Automaximize Value" to 100%. Disabling the Grid plug-in didn't do anything I can detect.

This is one of the weak spots of Unity: customization.

---

### Post by CrusaderAD on 2011-10-26
> **JRV said:**
> My installation defaulted to four desktops, so I can't help with that problem.

To disable the automaximize:

Open a terminal and enter this code:
```

sudo apt-get install compizconfig-settings-manager
ccsm

```
Near the bottom of the page, uncheck "Grid"

Then open the Ubuntu Unity Plugin under the Desktop heading.

Click on "Experimental" and change the "Automaximize Value" to 100%.
___

I did this, not working. I just want my windows to come back to the same state they were in. Who the f would want this option on a big screen?

---

### Post by JRV on 2011-10-26
> **lads said:**
> Thank you for the replies. I had already set the "Automaximize Value" to 100%. Disabling the Grid plug-in didn't do anything I can detect.

This is one of the week spots of Unity: costumization.

Unchecking Grid stops a window from automaximizing when it is dragged to the top of the screen.

---

### Post by JRV on 2011-10-26
> **CerealCypher said:**
> I did this, not working. I just want my windows to come back to the same state they were in.

Are you using Unity2d? Compiz is not active in 2d so ccsm won't do anything.  This is the only reason I know of why it wouldn't work.

>  Who the f would want this option on a big screen?
Good question!
Who would want this option on any screen?

---

### Post by lads on 2011-10-27
> **JRV said:**
> Are you using Unity2d? Compiz is not active in 2d so ccsm won't do anything.  This is the only reason I know of why it wouldn't work.

Hi again, I am using Unity 2D, because 3D doesn't work. So basically what you are telling us is that Unity 2D is not configurable/customizable?

This version of Unity, which at first sight looked as a good improvement, seems to have even more problems than the previous version. How can it ever be considered stable enough for a release?

Thanks to all for the replies anyway.

---

