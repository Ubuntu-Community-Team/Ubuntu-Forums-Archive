---
title: "Buggy Mouse and Interface After Hibernate"
date: 2009-06-08
forum: General Help
---

### Post by Noobs*McGee on 2009-06-08
Hi,

I'm running Ubuntu 9.04 Jaunty Jackalope on a Toshiba Satellite M45 with 1.60 GHz Intel Pentium M Centrino and 1 GB RAM (I'm not really a techie, so I don't really know much about it beyond that).  So far, Ubuntu has been working wonderfully, and for the most part I've had no regrets about switching from WinXP.  I've come across a few minor issues that were annoying or confusing, but for the most part fairly harmless and were easily solved with some (much appreciated) help from the Ubuntu community.  However, I've now run into a problem that is more than simply annoying and actually inhibits my computer use.

It seems that every time I close the lid on my laptop (which sends it into hibernation) and then return later and reopen it, my system suffers severe lag for some reason.  At first I thought it was just an issue with my wireless mouse, which produced extremely laggy motion in the cursor whenever my computer returned from hibernation, while my touchpad seemed to work normally.  However, disconnecting/reconnecting the wireless receiver and resyncing the mouse had no effect, and I noticed that certain elements of the GUI seemed to be adversely affected as well -- for example, when I click on an icon in the panel, it seems to sort of echo.  That is, the icon itself will depress and rebound multiple times (instead of just once) and the sound that usually accompanies clicking on the icon will be drawn out and repeat itself, much like an echo.

The only thing that seems to fix this is to restart my computer, which obviously is pretty inconvenient.  I'd really like to have the convenience of being able to put my computer into hibernation when I leave for a short time and return to continue working without having to restart my computer to get normal performance.

If anyone has an idea what might be wrong here, please let me know.  I really love Ubuntu and don't like the idea of returning to WinXP, but this problem may very well drive me to do so, as I use the hibernation feature on a regular basis and am not sure I want to give up its convenience, even if it means foregoing the headaches of WinXP.

Thanks in advance,
NM

---

### Post by moster on 2009-06-08
You can try put it in standby instead hibernate. S3 standby and hibernate only differ in keepeng RAM under power on standby. But I dubt it will help.
       For all I know they repair it in 8.10 (karmic koala). Maybe you can try it, but I do not recommend install it permanent, it is still alpha.
       I must have that installed on my HP laptop because that is first ubuntu that actually work as suppose to. Everything work at last.
       If you are curious, look at what they changed in latest alpha kernel, maybe there is some patch or something, I am not that advanced.

edit: sit tight, maybe someone will answer specifically to your problem.

---

### Post by Noobs*McGee on 2009-06-13
A couple small things to add:  first, I made a slight error in the original post: there is no "visual echo" in the icon, like a had said, I think I just imagined one, because of the sound (I'm fairly new to the system, so I'm not totally used to all the details of the interface yet).

There IS, however, a distinct lag/echo in the sound, and it doesn't just affect system sounds, but any and all sound output.  I tried playing some music while the system was in "laggy mode" and got the same effect: playback was very drawn-out and glitchy.

Additionally, I checked the system monitor to see if resource use was abnormally high, but everything seemed pretty normal.  I'm actually operating "in laggy mode" right now - the only things (so far) that seem to be affected are sound output and the wireless mouse input...

---

### Post by timjohn7 on 2009-10-24
I'm having a similar problem in Karmic Koala Beta.  Both wireless and wired (for testing) mice seem to lose focus unless I make an app "Always on Top".  I first noticed the wireless mouse losing focus when I had multiple tabs open in Opera, but even after closing Opera the problem persisted.

Restarting the computer fixed the problem temporarily, but after a while (10 minutes) the problem reappears.

I'm using the Labtec Wireless Desktop combination and the keyboard works 100% out of the box.  It's just the mouse that seems to be problematic.

---

