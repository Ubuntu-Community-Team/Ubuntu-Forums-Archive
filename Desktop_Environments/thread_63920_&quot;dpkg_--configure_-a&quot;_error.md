---
title: "&quot;dpkg --configure -a&quot; error"
date: 2005-09-09
forum: Desktop Environments
---

### Post by eljaco on 2005-09-09
Ok, so here it goes:
I have a Dell PowerEdge 400SC dual boot with Kubuntu and WinXP. I had been using the WinXP boot for the past few months and I finally got a new video card (ChainTech GeForce 6600) because it was just too painful. I installed the drivers on the WinXP part and decided I would configure my Kubuntu to the new video card now that I have some free time.
I believe I got everything to work as far as configuring the video card, but for some reason it started up Ubuntu with KDE (instead of Gnome) and I thought I would be a good idea to just update everything while I was at it. So I ran a smart update with Kynaptic, and after downloading all the new packages, it started to install but about a minute after it started, the computer froze. I shut it down, restarted it on Kubuntu (also KDE) and ran Kynaptic. I got this error:

!--
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
--!

So, I went to my terminal window and ran that command, but now I get this error:

!--
dpkg: parse error, in file `/var/lib/dpkg/updates/0024' near line 24 package `dbus-1':
 EOF during value of field `Description' (missing final newline)
--!

I have no clue what to do now. If you need more info on my system, let me know.

Thanks!

---

