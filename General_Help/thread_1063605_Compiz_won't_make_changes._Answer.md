---
title: "Compiz won't make changes. Answer?"
date: 2009-02-08
forum: General Help
---

### Post by janthonywj on 2009-02-08
Didn't get a response on the newbie section, so I came here:

Alright. Of course, I'm a newbie to the linux world, but not to the computing world. And, yes, I'm one of those guys that likes to waste system resources on ascetically pleasing graphics. [Eagerly awaiting Kubuntu to develop the animated wallpapers].

I'm at the end of my first day with Kubuntu 8.10. I've been running updates and messing around (installing wine, opera, Firefox, plug-ins, changing settings to remove screen flickers) off and on all day. I just can't figure this stupid problem out.

I just added a new repo in Adept,

[http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu)

, so I could get the new KDE 4.2. Ran the update, hit a snag, "unrecoverable error", with one of the updates, worked my way through it, it failed, but on the second attempt it was ok. SO, I then installed Compiz in Adept as well. I didn't really see any differences in my desktop environment (note: I had the option of using Compiz as my window manager already, but couldn't find a way to make alterations), but I had more options in the desktop preferences in my system settings menu after the install (That weren't there before I added the repo), a lot that I was looking for. Any changes I made made no difference in my desktop though. Then I refreshed the windows manager, and it screwed everything up so I restarted my computer. Upon returning, I had a new wallpaper, and transparent task-bar etc. So I figured I made a mistake and should have restarted naturally after updating so much. But now, making changes in the Desktop menu on System Settings still has no effect. I can't change anything. No window flipping, no transparency altering, nothing. To make things clear, I CAN change the settings, but they have no effect.

What do I do? Is there a compiz manager or something I can use, and if so I can't find it. All I can find is the Compiz Fusion Icon.

Running Kubuntu 8.10 (intrepid) with KDE 4.2
Trying to remember my specs offhand since I don't know how to look them up in my new environment yet:
Centrino 1.8 GHz, 1GB ram, Intel GMA915 chipset (I think)
Minimal for Vista, but should handle anything Linux throws at it.

---

### Post by gettinoriginal on 2009-02-09
You need CompizConfig Settings Manager it is in your repos, so just install it.  Then you will find it in your system preference settings.  :p

---

### Post by bunnyhugh on 2009-02-09
> **janthonywj said:**
> Didn't get a response on the newbie section, so I came here:

Alright. Of course, I'm a newbie to the linux world, but not to the computing world. And, yes, I'm one of those guys that likes to waste system resources on ascetically pleasing graphics. [Eagerly awaiting Kubuntu to develop the animated wallpapers].

I'm at the end of my first day with Kubuntu 8.10. I've been running updates and messing around (installing wine, opera, Firefox, plug-ins, changing settings to remove screen flickers) off and on all day. I just can't figure this stupid problem out.

I just added a new repo in Adept,

[http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu)


, so I could get the new KDE 4.2. Ran the update, hit a snag, "unrecoverable error", with one of the updates, worked my way through it, it failed, but on the second attempt it was ok. SO, I then installed Compiz in Adept as well. I didn't really see any differences in my desktop environment (note: I had the option of using Compiz as my window manager already, but couldn't find a way to make alterations), but I had more options in the desktop preferences in my system settings menu after the install (That weren't there before I added the repo), a lot that I was looking for. Any changes I made made no difference in my desktop though. Then I refreshed the windows manager, and it screwed everything up so I restarted my computer. Upon returning, I had a new wallpaper, and transparent task-bar etc. So I figured I made a mistake and should have restarted naturally after updating so much. But now, making changes in the Desktop menu on System Settings still has no effect. I can't change anything. No window flipping, no transparency altering, nothing. To make things clear, I CAN change the settings, but they have no effect.

What do I do? Is there a compiz manager or something I can use, and if so I can't find it. All I can find is the Compiz Fusion Icon.

Running Kubuntu 8.10 (intrepid) with KDE 4.2
Trying to remember my specs offhand since I don't know how to look them up in my new environment yet:
Centrino 1.8 GHz, 1GB ram, Intel GMA915 chipset (I think)
Minimal for Vista, but should handle anything Linux throws at it.

If your are running KDE4.2 as you say, then you don't need compiz to get desktop effects, as the upgraded window manager now has compositing built into it with its own set of controls/switches. 

To turn on effects go to "System Settings" -> "Desktop" highlight "Desktop Effects" in the left hand window, then click the "All Effects" tab in the right hand window, turn/off what every your like. You can remove the compiz specific packages that you installed, (or leave then if they don't cause any problems).

As you don't seem to be able to change anything, I would check that you have the right version of library "libplasma" installed. KDE4.2 uses "libplasma3" but if you have installed compiz settings manager I believe this uses "libplasma2" which conflicts.

Sorry I can't be of anymore help.

Rgds

---

