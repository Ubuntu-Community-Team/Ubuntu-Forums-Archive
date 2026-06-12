---
title: "How can I install ATI drivers in Natty 11.04"
date: 2011-11-26
forum: Desktop Environments
---

### Post by Acharn on 2011-11-26
OK, I have an ATI Radeon x1550 graphics card in an Acer Aspire 1610 running Natty Narwhal 11.04. I found a how-to for installing ATI binary drivers, but it was concerned with Catalyst 11.2. When I go to the ATI support page, they indicate that the x1550 requires a legacy driver, Catalyst 9.3. So I download it and follow the instructions in the how-to and I get: 

"Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.38-12-generic;"

I haven't been able to find another thread about the Radeon x1550, but I've found some old threads talking about Ubuntu 8.x or 9.x, which don't have any solution. Is there any way to install the ATI fglrx driver with my graphics card?

---

### Post by Frogs Hair on 2011-11-26
Are there any drivers available via additional drivers ? If so that would be the best option .

---

### Post by coffeecat on 2011-11-26
> **Acharn said:**
> Is there any way to install the ATI fglrx driver with my graphics card?

Basically, no. Have a look here:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

The legacy fglrx driver that can run that card is only compatible with versions of the xserver that came with now-obsolete versions of Ubuntu - pre-February 2009 as that link says. Which means Ubuntu 8.10 or earlier, or possibly 9.04, as you have found.

However, the default open source driver might be able to give you enough 3d acceleration with your x1550 card to run the Unity desktop. Can you run the Unity desktop in 11.04, or does it fall back to classic gnome when you log in?

---

### Post by Acharn on 2011-11-26
It runs the Unity desktop, which I really like. In fact one reason I haven't upgraded to 11.10 is the number of comments I've seen about problems with the Gnome desktop -- I don't want to give up the Unity desktop. The reason I wanted to use ATI drivers is that I have problems trying to run Windows games in Wine. Programs that I easily ran under Windows XP have problems with serious mouse lag or not showing text on the screen or not showing any graphics detail.

---

### Post by coffeecat on 2011-11-27
> **Acharn said:**
> It runs the Unity desktop, which I really like. In fact one reason I haven't upgraded to 11.10 is the number of comments I've seen about problems with the Gnome desktop -- I don't want to give up the Unity desktop.

I'm not sure I follow you. 11.10 comes with Unity 3d and 2d only in a default install. Your card should be able to run Unity 3d in 11.10 if it can do so in 11.04, but if it can't, it will fall back to Unity 2d. 11.10 is based on gnome3 where 11.04 was based on gnome2, but that shouldn't prevent you from running Unity. If you have any doubts, download the 11.10 ISO, burn a CD and run 11.10 live.

Sorry I can't help you with wine and Windows games.

Good luck!

---

### Post by Acharn on 2011-11-27
> **coffeecat said:**
> I'm not sure I follow you. 11.10 comes with Unity 3d and 2d only in a default install. Your card should be able to run Unity 3d in 11.10 if it can do so in 11.04, but if it can't, it will fall back to Unity 2d. 11.10 is based on gnome3 where 11.04 was based on gnome2, but that shouldn't prevent you from running Unity. If you have any doubts, download the 11.10 ISO, burn a CD and run 11.10 live.

Sorry I can't help you with wine and Windows games.

Good luck!

OK, that does that research for me. I had just been putting off checking it out because I've got these other problems I'm working on. I got the impression Gnome was the default desktop in 11.10, and had been meaning to read up on it but haven't had time. My DVD writer doesn't read DVDs and won't play CDs, too. So I'll try upgrading and maybe that will solve some of my other problems. Meanwhile, I wonder if installing driconf and tweaking some of the settings would help with the video. I see driconf has only 3 stars from its reviewers.

---

### Post by thaelim on 2011-11-28
driconf is for adjusting very low-level graphics driver settings in the open-source drivers, mainly around vertical sync for the monitor. It is only good if you are experiencing problems with vertical sync (and even then, usually applications or display drivers will override whatever setting you configure with driconf). Hence the 3 star rating, I suspect.

---

### Post by mastablasta on 2011-11-28
> **Acharn said:**
> It runs the Unity desktop, which I really like. In fact one reason I haven't upgraded to 11.10 is the number of comments I've seen about problems with the Gnome desktop -- I don't want to give up the Unity desktop. The reason I wanted to use ATI drivers is that I have problems trying to run Windows games in Wine. Programs that I easily ran under Windows XP have problems with serious mouse lag or not showing text on the screen or not showing any graphics detail.
 
if you run Unity with 3Dsupport (hardware acceleration) this could cause the problems in wine (Compiz on odl gnome could do the same thing - interfere with wine). try unity 2D or gnomefallback or try another DE (XFCE!? - Xubuntu) and see if problems persist. in fact unity messes up with a lot of stuff onscreen and wine games.
 
also regarding wine if possible try to use OpenGL instead of DirectX. and make sure you read all instructions on wine site (sometimes certain desktop shortcuts also interfere with games). desktop should run under programmes and unnoticed, but that is not the case in linux with wine.

---

