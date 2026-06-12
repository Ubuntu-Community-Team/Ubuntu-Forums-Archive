---
title: "How to remove Murrine themes?"
date: 2011-09-22
forum: Desktop Environments
---

### Post by The_Autonomist on 2011-09-22
Does anyone know how? I have like 10 of them in my Appearance, and I never use them. I would like to free up space and have only themes i plan on using in Appearance manager. 

Help?

---

### Post by ibutho on 2011-09-22
I doubt you will save much space by removing them because the actual murrine package is only a few megabytes in size. If you want to remove then, search for murrine and murrina in Synaptic and uninstall from there. Beware that other themes may rely on the murrine engine, so if uninstalled, those themes won't work well.

---

### Post by mcduck on 2011-09-22
> **The_Autonomist said:**
> Does anyone know how? I have like 10 of them in my Appearance, and I never use them. I would like to free up space and have only themes i plan on using in Appearance manager. 

Help?

How did you install them? If you got them from some repository, through the package management, then the package management is also ho you can uninstall them.

If you downloaded them yourself, just delete their directories from ~/.themes (or /usr/share/themes if you installed them system-wide).

---

### Post by The_Autonomist on 2011-09-22
Well now I have a bigger problem...........

I removed the Murrine themes via Synaptic Package Manager (just the theme packs, not the engine), but i was also removing some other ones out of my Appearance manager and all of a sudden my Appearance Manager window froze up. It wouldn't let me close it either, so i tried to open System MOnitor to force it close and it wouldn't let me open that either. So, i rebooted, and tried to open Appearance settings again...all it will do is open and then close again really quickly. Like a flash. System Monitor is doing the same thing, i can't open Synaptic either. I can open my FF browser and folders just fine. 

So, i tried to open Appearance manager through terminal, and i got this massive error message having something to do with New Wave (the theme.) I've attached a screenshot below. IN the screenshot, you can see the error message, as i said it's EXTREMELY long so i didn't want to post the entire thing. You see how the numbers start in the 3000's? They go all the way to the 5000's....saying that it's unable to locate various image files and such.

I tried to open nautilus as root in order to completely delete the New Wave folder, but it won't let me open nautilus as root. My mouse arrow will appear to be working and then it'll just turn back to normal. 

As of right, i cannot change my themes, use my terminal (without getting this long error message), gain root privileges, or even open Synaptic. Does anyone know what happened? I assume i caused this somehow when i was deleting a theme through Appearance properties. Also, my scrollbar won't appear right, and neither will button outlines...

---

### Post by The_Autonomist on 2011-09-22
UPDATE: SO, i solved most of my problem using this thread [http://ubuntuforums.org/showthread.php?t=1817657&highlight=appearance](http://ubuntuforums.org/showthread.php?t=1817657&highlight=appearance). I uninstalled and reinstalled the New Wave/Dust package and I no longer receive the error message in my previous post when i attempt to use terminal.

I can now open Appearance and Synaptic. BUT, i still can't gain root privileges. I keep opning my terminal and typing in "gksudo nautilus" but i receive this error message:

> (nautilus:3151): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
I'm trying to gain root, so i can go to usr/share/themes and delete some themes the right way this time, not via appearance manager. But, it won't let me gain root...

---

### Post by Krytarik on 2011-09-22
If, or when, you finally decide that breaking the system for saving just a few megs, by especially removing the default themes, isn't really worth it, you can fix your system this way:

1. Boot into "recovery mode -> netroot" (you may need to press Shift to make the boot menu appear).

2. Reinstall the packages "gnome-themes-ubuntu" and "light-themes" (no need of 'sudo' here, as you will already be root):
```
apt-get install --reinstall gnome-themes-ubuntu light-themes
```
3. Reboot by pressing Ctrl+Alt+Delete.

Greetings.

---

### Post by The_Autonomist on 2011-09-22
Thank you, i'll try your solution out. ;)

But, just for clarification, when i said "space" i didn't mean actual disk space. I meant, that I had a slew of default themes in my Appearance that I never used/planned on using and I got tired of having to sift through 20 themes I don't want to get to the ones i did want to use. It's way too cluttered...

---

### Post by Krytarik on 2011-09-22
> **The_Autonomist said:**
> But, just for clarification, when i said "space" i didn't mean actual disk space. I meant, that I had a slew of default themes in my Appearance that I never used/planned on using and I got tired of having to sift through 20 themes I don't want to get to the ones i did want to use. It's way too cluttered...
Yeah, I took as much as well. But still, not worth it! ;-)

---

### Post by The_Autonomist on 2011-09-22
Thank you!! It worked, i'm all fixed up now. :P

---

