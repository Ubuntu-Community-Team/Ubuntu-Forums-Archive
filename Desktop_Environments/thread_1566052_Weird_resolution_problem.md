---
title: "Weird resolution problem"
date: 2010-09-01
forum: Desktop Environments
---

### Post by tarahmarie on 2010-09-01
Hi, all:

Since I switched to a Sony Bravia 48" monitor (I sit a bit back from it in a recliner), I'm having the weirdest resolution issues.

I use an Nvidia 8600 GeForce, Lucid, and KDE.  I've tried changing the system font, but it has to be at 64 points or better to even read it. Meanwhile, my windows have totally illegible tiny fonts in the titlebars, I have to scroll in 3x or 4x to read anythign in Firefox...you get the idea.

The problem is that I don't really know where to start in fixing this problem. Is there a driver I'm supposed to be using? Where's the settings to fix this? More, how the devil do I READ those settings when I can't see them.  Look at the attached screenshot; I've tried to show you how screwed up this is.

I tried executing 

```

xrandr -s 1024x768

```

But it didn't help.

Any ideas?

Thanks!

---

### Post by usagiakumu on 2010-09-01
I have tried both Ubuntu and Kubuntu. I use a GTX 260 with a nice large monitor at a high resolution. The issue seems to lie in KDE and KDE apps. None of the GTK apps I use have these issues. When I use a QT app even in Gnome it does the same thing you are experiencing. I suggest the regular vanilla Gnome based Ubuntu. As one of my friends who introduced me to Linux says "friends don't let friends use KDE", so my suggestion is to drop it and use Gnome. I would rather have a stable working desktop 99% of the time than a hundred half done options I never use 99% of the time anyway. There is a reason KDE isn't supported by the main demographic of developers who make this wonderful OS.:KS

---

### Post by tarahmarie on 2010-09-01
> **usagiakumu said:**
> I have tried both Ubuntu and Kubuntu. I use a GTX 260 with a nice large monitor at a high resolution. The issue seems to lie in KDE and KDE apps. None of the GTK apps I use have these issues. When I use a QT app even in Gnome it does the same thing you are experiencing. I suggest the regular vanilla Gnome based Ubuntu. As one of my friends who introduced me to Linux says "friends don't let friends use KDE", so my suggestion is to drop it and use Gnome. I would rather have a stable working desktop 99% of the time than a hundred half done options I never use 99% of the time anyway. There is a reason KDE isn't supported by the main demographic of developers who make this wonderful OS.:KS

I hear you, but I happen to ADORE KDE.  I love the simplicity, the maneuverability, and the full features. I love the plasmoids. I love Kate, and I LOVE the Compiz integration. 

I'd rather just fix this issue. I've had similar issues before with huge LCDs, but that's not usually an issue with the DE--just usually an issue of finding where the settings are that need to be adjusted.

PS: I'm totally trying out OpenSuSE and Enlightenment in my play partition.  We'll see how that works.

---

### Post by usagiakumu on 2010-09-02
I actually find KDE to be overly complicated, where Gnome keeps it simple. EFL is another GDI entirely. While I may not know much about Linux, I know a bit about graphics and vector GDI interface. I spent a lot of time coding for Windows and Mac. It seems that the issue relies in the drivers itself and QT. A lot of people complain about the drivers being closed source, but refuse to look at the white sheets provided by NVIDIA. They will then go code all willy-nilly and expect everyone to bend to their will. I agree that the drivers should be open source, and it may be easier for them to be so, but the fact is they aren't. The white sheet with all of the information provided exists so you can code around some of the discrepancies. QT and KDE developers refuse to do this, I have put a little research into what I am saying. While the fault rests with NVIDIA, FOSS devs should go out of their way to make things work rather than doing "whats fun". It is why I prefer GNOME, with no desktop effects as they are incompatible with a few things. Cool as they may be, I even turn everything off in Windows 7 as desktop effects amuse simple minds and are really pointless after the 9 millionth time of seeing them. I am one for a good theme though.

---

