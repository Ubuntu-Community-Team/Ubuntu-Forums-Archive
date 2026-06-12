---
title: "System tray icon order changes after reboot"
date: 2010-12-03
forum: Desktop Environments
---

### Post by stickyfoot on 2010-12-03
Ubuntu 10.10, fairly fresh install.

The order of the icons in the system tray changes each time I reboot. It's worked fine since install a few weeks ago until today when I booted and the wireless wouldn't connect. I rebooted and they came up in a different order so I rebooted again and the order changed yet again. 

Maybe I should just keep rebooting until I find an order I'm happy with then never switch my machine off.

I've attached a printscreen to show what I mean. If anyone can point me in the direction of a solution I would be very appreciative.

---

### Post by Frogs Hair on 2010-12-03
You could try right clicking the icon , moving it to the position you want , then right click and lock to panel. I have not found a good explanation as to why they move to begin with.

---

### Post by stickyfoot on 2010-12-04
> **stickyfoot said:**
> The order of the icons in the system tray changes each time I reboot.

UPDATE: The order of the icons has settled down now to the same (but wrong) order so I'm going to try rearranging them manually and see if they stay.

One possible trigger is that I connected an external monitor so maybe that was responsible.

The problem I have now is that upon waking from hibernation the Ubuntu 'skin' which makes Gnome look like Ubuntu has now gone and my laptop function buttons don't work.

Can anyone tell me which file/process is responsible for that so I can look to see if if is corrupted?

---

### Post by fastcrab on 2010-12-18
I see this every day in gnome panel.

Staying in a hotel without an external monitor and have to re-arrange the taskbar icons to get to a resemblance of normal.  Appears to be random ordered, has affected the time/date, trash can, workspace switcher, network manager, cpu frequency scaler, indicator applet, etc etc.  So I arrange my icons and am happy until going to work the next day.

I plug the laptop into a monitor, TV, or projector at work.  At least half of the panel icons are in a place I have never seen them. They do not switch from the top to bottom panel, but they do seem to go left or right in random amounts.  I haven't seen them messed up in the same way twice.  The icons are definitely not where I expect them to be.

I have tried locking all icons, unlocking all icons, either way - I need to rearrange most of them after rebooting with some part of the equation relating to an external monitor.

I tried to just accept that my gnome panel settings would just be random every day, but it isn't working.

---

### Post by chower on 2011-03-28
I'm seeing this too, not a huge deal, but a bit annoying.  Anyone have any idea on how to troubleshoot this?  I'm assuming it has something to do with loading order since all these pieces show status of running processes, so for example, if the wireless takes longer to start up it goes in a different spot?

---

### Post by Krytarik on 2011-03-28
> **chower said:**
> I'm seeing this too, not a huge deal, but a bit annoying.  Anyone have any idea on how to troubleshoot this?  I'm assuming it has something to do with loading order since all these pieces show status of running processes, so for example, if the wireless takes longer to start up it goes in a different spot?
We need to differentiate here, between the order of
- applets: Those should generally not change, unless their positions are not locked or the screen resolution has been changed.
- items in the notification area: To those applies what you said, they get placed in it dependend on when their startup process is finished.

---

### Post by chower on 2011-03-28
> **Krytarik said:**
> We need to differentiate here, between the order of
- applets: Those should generally not change, unless their positions are not locked or the screen resolution has been changed.
- items in the notification area: To those applies what you said, they get placed in it dependend on when their startup process is finished.

Ok, here's a screenshot showing what I'm talking about.  See how the power button is in the middle and the date is on the left.  The order of these things appears random even though I have them all set to lock to panel.

---

### Post by dacoolio on 2011-03-28
That doesn't appear to be caused by varying startup times, since it would only affect the system tray if that were the case. What is the resolution of the monitor you're using? If it has a weird setting, that might be tripping it up?

---

### Post by chower on 2011-03-28
> **dacoolio said:**
> That doesn't appear to be caused by varying startup times, since it would only affect the system tray if that were the case. What is the resolution of the monitor you're using? If it has a weird setting, that might be tripping it up?

It's a laptop running 1440x900.  Like one of earlier posters, it seems to happen most often when using the external VGA port.  I teach classes and hook up to projectors, often needing to adjust the resolution to something like 1024x768 so it looks decent to the class.

---

### Post by Krytarik on 2011-03-28
> **chower said:**
> It's a laptop running 1440x900.  Like one of earlier posters, it seems to happen most often when using the external VGA port.  I teach classes and hook up to projectors, often needing to adjust the resolution to something like 1024x768 so it looks decent to the class.
Then we have the reason, although no solution, there seems to be none.
> **Krytarik said:**
> 
- applets: Those should generally not change, unless their positions are not locked or the screen resolution has been changed.


---

