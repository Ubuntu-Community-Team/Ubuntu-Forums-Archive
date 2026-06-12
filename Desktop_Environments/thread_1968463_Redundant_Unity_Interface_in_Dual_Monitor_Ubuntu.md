---
title: "Redundant Unity Interface in Dual Monitor Ubuntu"
date: 2012-04-29
forum: Desktop Environments
---

### Post by blitzit on 2012-04-29
I have a dual-monitor workstation which had ubuntu 10.04 until 3 days back when I upgraded to 12.04.

I still have the workstation running, now with 12.04, but now both the monitors have the unity interface sticking to them (have attached a screenshot for reference), unlike how the menu used to be in the primary monitor earlier. Is there way I can clear the clutter from one of the screens?

P.S.: I have installed proprietary NVIDIA drivers. Before doing this, ubuntu gave me the same image on both my monitors.

---

### Post by howefield on 2012-04-29
Go to System Settings > Displays and change as required.

---

### Post by blitzit on 2012-04-29
Cool! It had somehow missed me :)

Thanks a ton!

---

### Post by confy on 2012-04-29
What to do if "Laptop" screen is only right screen and you can place "Launcher" only on middle of right screen?

Here is funny screenshot:

---

### Post by blitzit on 2012-04-29
In NVIDIA X Server Settings, in the X Server Display Configuration, in Display play around with the Position value of the screens. You should be able to figure out the correct layout applicable to your configuration.

To be able to save the configuration, you will need to run this program as root. To do this you will need to give:

```
$ sudo nvidia-settings
```

(You probably know the command already, otherwise you wouldn't have reached here :) )

---

### Post by blitzit on 2012-04-29
Just curious, what is the thing to the right edge of your screenshot - the one which mentions system stats? :) Interesting add-on :)

---

### Post by howefield on 2012-04-29
> **blitzit said:**
> Just curious, what is the thing to the right edge of your screenshot - the one which mentions system stats? :) Interesting add-on :)

Looks like conky.

Here's a thread devoted to it...

[http://ubuntuforums.org/showthread.php?t=281865&page=1966](http://ubuntuforums.org/showthread.php?t=281865&page=1966)

---

### Post by Eklipze3k on 2012-05-09
Thanks for this, just installed 12.04 and am just getting used to it. Is there anyway to stop the mouse 'freezing' when going from screen1 to screen2?

Edit: Ignore me, just saw the option in the same screen :oops:

---

