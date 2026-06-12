---
title: "Power management/hibernation problem"
date: 2009-04-10
forum: General Help
---

### Post by Thorndog on 2009-04-10
I have a problem on my desktop: I tell it to never go to sleep in power management but set the screensaver for two hours as that is the longest. Seems that the screensaver kicks in and then my system bugs out and shuts off completely. When I hit the power button to start it up again the next time I come along, it eventually comes up with a re-log in box and when it restores, the internet and  music don't work. I get a message in the lower right corner telling me that the system failed to go to sleep properly..... well I told it not to go to sleep in power management (only because it doesn't wake up properly, I'd love to save power!!) so I don't seem to have any more options.
My swap space is much bigger than RAM as you can see (unless I am reading it wrong):
total       used       free     shared    buffers     cached
Mem:     917540864  905912320   11628544          0  118067200  288755712
-/+ buffers/cache:  499089408  418451456
Swap:   3084439552   45699072 3038740480
I can't leave my system running with downloads or anything else long term running.
Help please.

---

### Post by acimmarusti on 2009-04-10
Do this and tell me what you get:

```
cat /sys/power/image_size
```

if you get much less than the size of your total ram memory as evidenced by the *free -b* command, then you need to change that by doing this:

```

sudo -i
gedit /etc/rc.local

```

Once gedit is opened, add this line before *exit 0*: 

> echo 917540864 > /sys/power/image_size

Now, restart and try hibernating!. Hibernating works on my laptop, but suspend does not (if you have any proprietary drivers installed (ATI, NVIDIA, broadcom, etc) suspend will never work. At least not on intrepid.

Hope this helps

---

### Post by Thorndog on 2009-04-14
Andres,
thanks for the help. The image size was smaller, I made the changes you suggest and it seems to make some small difference as in: sometimes it doesn't shut off when left alone for a while.
I think it is the suspend that causes the problem. Meanwhile, of course the setting I have in pwr mgmnt is to never sleep, clearly that utility is not working. Gnome Help sais to report it as a bug because it's supposed to just work. 
I have a feeling however that some combo of NVIDIA drivers and Atheros HAL and  wireless drivers is screwing things up, especially as the wireless is one of the things that doesn't usually work after awakening from suspend. I don't think that reporting it as a bug will help anyone.
My old XP Toshiba high end laptop had the same sort of problems with sleep and waking up right out of the box as shipped. Never did resolve that..... Seems to be a problem area for many OSs and hardware combos. Come to think of it, my little ACER netbook with Linpus has severe sleep and waking up problems.
Come to think of it, I have the same sorts of problems :-} Never was too good at mornings.

---

