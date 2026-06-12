---
title: "XFCE display issues with OpenOffice"
date: 2010-08-08
forum: Desktop Environments
---

### Post by ugm6hr on 2010-08-08
I've been using Xubuntu 10.04 on my Mini 9 for a few months. No major problems, but this one is a little frustrating.

To reproduce:
1. Install OpenOffice on XFCE4 / Xubuntu
2. Launch OpenOffice Word
3. Select menu View->Zoom

The Zoom window opens, but is "see-through" i.e. nothing appears within the window, but you can see through it to whatever is behind. I have attached an example of the "Screenshot" app behind.

To correct:
1. Maximise, then minimize the Zoom window.

This also affects a number of other OO.org functions, including OO.org Base forms (which is very frustrating for me), although this displays windows in an even weirder fashion (see other screenshot attached.

Any ideas? I can't find this as a bug.

---

### Post by ajgreeny on 2010-08-08
Compiz running or not?  Seems like that sort of problem.

---

### Post by ugm6hr on 2010-08-08
> **ajgreeny said:**
> Compiz running or not?  Seems like that sort of problem.

Nope.

compiz-core not installed, so can't even do that by accident.

---

### Post by cascade9 on 2010-08-08
I thought compiz as well, but that is ruled out. 

It might be a Xubuntu issue. Using sidux ATM, Xfce version, fully updated, and I get the 'zoom' widow fine.

Xfce 4.6.2, OO 3.2.1

---

### Post by ugm6hr on 2010-08-08
> **cascade9 said:**
> It might be a Xubuntu issue. Using sidux ATM, Xfce version, fully updated, and I get the 'zoom' widow fine.

Xfce 4.6.2, OO 3.2.1

Xubuntu 10.04 is XFCE 4.6.1 / OO 3.2.0

Maybe you are right.  I'm going to boot into Gnome to confirm it is XFCE specific.

EDIT: Yep - works fine in Gnome. Clearly a XFCE feature.

---

### Post by cascade9 on 2010-08-08
Silly question, but you dont have the Xfce compositor turned on?

*edit- it would be interesting to see if a minmal Xfce had the same issue as (I'm assuming) xubuntu-desktop.

---

### Post by ugm6hr on 2010-08-08
No - XFCE Compositor off (Window Manager Tweaks setting).

Just tried it on - still the same problem.

---

### Post by azertyh on 2010-08-08
hi,
i have ubuntu 10.04 but installed xfce 4.6.1, just the window manager. no compiz, compositor on. no problem with the zoom in writer.

---

### Post by ugm6hr on 2010-08-08
> **azertyh said:**
> hi,
i have ubuntu 10.04 but installed xfce 4.6.1, just the window manager. no compiz, compositor on. no problem with the zoom in writer.

Hmmmm.... Maybe something Xubuntu specific...

Or related to my Mini 9 Graphics card.

---

### Post by Hagar Delest on 2010-08-08
Never had any issue with xubuntu. Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by ugm6hr on 2010-08-08
> **Hagar de l'Est said:**
> Never had any issue with xubuntu. Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Waiting for someone to confirm they have the same issue before trying to fix it by messing with my system at this stage.

I quite like using apt for the update system.

---

### Post by Hagar Delest on 2010-08-08
First time I see that issue in forums. I don't think you'll have any confirmation...

Try perhaps to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

Is it a standard installation of xubuntu?

---

### Post by ugm6hr on 2010-08-08
It was Ubuntu + xubuntu-desktop. From the standard repo.

Renaming the user folder didn't change anything.

---

### Post by Hagar Delest on 2010-08-09
I'm not sure that installing the xubuntu-desktop packages in addition to an initial Ubuntu install is the same as a blank xubuntu install. I've experienced some strange things when doing that. I don't remember such bugs but small hints showing that the effect was not exactly from the current session.

---

### Post by jgratero on 2011-02-16
Same issue over, here, Xubuntu 10.04, OpenOffice 3.2... Any updates on this one?

---

### Post by ugm6hr on 2011-02-17
I never fixed it.
Ended up moving to Gnome when I upgraded to 10.10 - its no longer a problem.

---

### Post by scramblejams on 2011-02-17
Same problem here. Not just maximizing but also resizing, does all sorts of weird things. I fled from Gnome because of some unrelated issues, and I like XFCE so I don't want to change. Enabling or disabling compositing hasn't helped.

The problem isn't necessarily Ubuntu-specific, I'm on Debian unstable. Don't know if it matters, but I'm using an Nvidia card with the closed-source driver. No other app I've tried seems to exhibit this issue.

Steve

---

