---
title: "I want the 11.04 Classic Ubuntu UI back"
date: 2011-10-15
forum: Desktop Environments
---

### Post by SkyeFerret on 2011-10-15
So how would I go about this?

My laptop isn't really made for graphics-heavy stuff, and Unity (or whatever it's called now) is really quite annoying to use.

[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961) < Gives me the GNOME UI, close to what I'm looking for, but not quite.

---

### Post by Spr0k3t on 2011-10-15
The information given in the thread linked is the closest you are going to get to the classic gnome 2.32 without rolling back to 11.04 or moving to another distribution.  What specifically are you missing, perhaps I can help you find some of the functionality.

---

### Post by mips on 2011-10-15
Xubuntu 11.10 is really nice and being adopted by many ex gnome 2.3 users.

---

### Post by Dry Lips on 2011-10-15
> **Spr0k3t said:**
> The information given in the thread linked is the closest you are going to get to the classic gnome 2.32 without rolling back to 11.04 or moving to another distribution.  What specifically are you missing, perhaps I can help you find some of the functionality.

For one thing the Ubuntu logo in the left corner is missing. Personally
I would also love the fallback mode to look like the fallback mode in
Fedora, which wasn't too bad.

Perhaps it'll be better if you install the entire Gnome Shell package as
well as the Gnome themes, which is described here... I'm going to try
that myself...

[http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/](http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/)

---

### Post by SkyeFerret on 2011-10-15
> **Spr0k3t said:**
> The information given in the thread linked is the closest you are going to get to the classic gnome 2.32 without rolling back to 11.04 or moving to another distribution.  What specifically are you missing, perhaps I can help you find some of the functionality.

I'm going to just move to Unity, then, or just roll back. Sorry to sound stubborn, but the UI I got from that link isn't at all what I'm trying to find. :/ Thanks, though, guys. Keep discussing if you want.

---

### Post by drawkcab on 2011-10-15
If you stay with 11.10 your immediate options appear to be to use gnome shell or move to xubuntu (xfce 4.8 is very nice and 4.10 will be here by January).  I think it will be a while before gnome fall back mode has the same functionality as gnome 2.  That said, gnome 3 has some really nice advantages under the hood (as does kernel 3.0)

The other option, of course, is to hang back for a year or so on 10.04-11.04 or move to a debian-based distro like Linux Mint Debian which will support gnome 2.x for a few more years.  LMDE is a pretty nice  option for gnome 2.x lovers (and features kernel 3.0) although you will have to get used to doing a couple things differently.

I love gnome 2.x too but the writing is on the wall insofar as the developers are no longer supporting it.

---

### Post by Dry Lips on 2011-10-15
Well, take a look at how nice the fallback mode can be once you use the
adwaita theme:


sudo ```
apt-get install gnome-themes-standard
```
Then install adwaita theme by right clicking on the desktop, etc.

---

### Post by kurt18947 on 2011-10-15
Have you looked at Ubuntu 11.10's fallback? You can get it by installing a single package, I think it's "gnome-fallback-session" or something like that. If you have Synaptic, put "fallback" in the search box and it should come up.  The fallback mode has "applications" & "places".  {working from memory here} The "System" menu is absent; the functions seem to be split between Applications -> other and "System ?" under the 'light switch' icon in the upper right corner.  You can also add Xfce-desktop and I think LXDE-desktop from Synaptic.  If you download either or both packes, install them then log out (I'd probably restart just for luck) then click on the gear next to your user name.  You should be able select your preferred window manager there.

---

### Post by HDTimeshifter on 2011-10-15
Is it possible to have the 11.10 fallback or the link above work so that you can switch back and forth, or at the very least have the option to select Gnome or Unity at boot time, or better yet to switch back and forth in real time?  I'd like to give Unity a try, and don't want to permanently revert to Gnome (yet).

---

### Post by HDTimeshifter on 2011-10-15
Is it possible to have the 11.10 fallback or the link above work so that you can switch back and forth, or at the very least have the option to select Gnome or Unity at boot time, or better yet to switch back and forth in real time?  I'd like to give Unity a try, and don't want to permanently revert to Gnome (yet).

Also, will the install default to a Gnome fallback like in 11.04?  I recently swapped out the disks in my file server (an old Athlon) that used to run 11.04 desktop (worked fine - didn't want to go down to low server command lines) and was waiting for 11.10 release to do a clean install, but don't want some non-usable GUI to install.  Or should I install 11.04 instead?

---

### Post by SatanSpawn on 2011-10-15
Why exactly is Unity such a pain in the ****??? i can't find gnome-terminal, none of my wine programs have names in the shortcuts "fail" thing, and i can't run Nvidia-Settings any more... I'm contemplating going back to windows... at least i know i can change my system setting there!!!!!!!!!   BTW I HATE Unity... and forcing us to dump Gnome 2.x was a bad move on Ubuntu's part if my opinion matters to any one.   We should be given the option to work with outdated software if we want, i have friends that still use KDE 3.5 for the god's sake... C'mon!  :mad:

---

### Post by HDTimeshifter on 2011-10-15
I'm kind of surprised about the "force Unity down our throats" thing also.  I thought one of the greatest benefits of Linux was the ability to run or switch between whatever GUI we liked - Gnome, KDE, or whatnot, instead of being forced to assimilate to to Windoze or Mac...resistance was not futile - the result was Linux...

---

### Post by drawkcab on 2011-10-15
For the umpteenth time, Ubuntu is not forcing anyone to dump 2.x *per se*.  

Gnome 2.x's obsolescence is due to the fact that the Gnome project is moving on to Gnome 3.x so that 2.x will no longer be supported.  To be clear, Gnome doesn't take orders from Ubuntu.

You don't have to like any of this but you do have to realize that Gnome 2.x's days are numbered; that you'll have to settle on a next-best alternative at some point anyway.

---

### Post by MarjaE on 2011-10-15
I've just tried out Xubuntu earlier today. It definitely seems to work, and to have the features I've used in Gnome 2 and not found in Unity. Now I'm still considering my options, and a Ubuntu/Xubuntu 11.10 hybrid doesn't sound bad ... I'm not sure how someone could safely install Xfce in standard Ubuntu 11.10, and I'm more confident about using Xubuntu or another Xfce-centered installation from another distro.

---

### Post by drawkcab on 2011-10-16
Xubuntu's a fine distro and you can install and use some elements from gnome.

---

### Post by waratah on 2011-10-16
Problem is the usability of Unity is not great.

Without reading a manual or searching I cannot work out how to add an element to the bar on the side or move the bar from the side to the bottom where I like it.

---

### Post by robert shearer on 2011-10-16
> **waratah said:**
> Problem is the usability of Unity is not great.

Without reading a manual or searching I cannot work out how to add an element to the bar on the side 
Open the app and its icon appears in the launcher.Right click on the icon and choose.."keep in launcher".

> or move the bar from the side to the bottom where I like it.
You can't. Mark Shuttleworth has decided that the launcher must always be on the left of the screen.
It is a like it or lump it feature.

If you wish a conventional panel arrangement and the ability to have a panel placed wherever you want then see this tutorial.
[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

If you do run that desktop then know that to customise it you must **alt+**right click on panels to select changes.

---

### Post by HDTimeshifter on 2011-10-16
> **robert shearer said:**
> You can't. Mark Shuttleworth has decided that the launcher must always be on the left of the screen.
It is a like it or lump it feature.

That's not good.  Even Windows let's you move their app toolbar form the bottom to the side.

---

### Post by DeMus on 2011-10-16
> **drawkcab said:**
> 

The other option, of course, is to hang back for a year or so on 10.04-11.04 or move to a debian-based distro like Linux Mint Debian which will support gnome 2.x for a few more years.  LMDE is a pretty nice  option for gnome 2.x lovers (and features kernel 3.0) although you will have to get used to doing a couple things differently.

I love gnome 2.x too but the writing is on the wall insofar as the developers are no longer supporting it.

I can tell you one thing: using Mint takes far less getting used to for a former Ubuntu user than it is to master Unity and/or Gnome 3. I would suggest all people to start using Mint, so you simply can continue the way you always did go.
Show developers we don't want Unity and we don't want Gnome 3.

---

### Post by HDTimeshifter on 2011-10-16
I take it Gnome 3 never made it to Ubuntu?  That's when they moved to Unity instead of Gnome 3?

I tried out Xubuntu on an old P2-400, and it wasn't any faster than Ubuntu 10.11 (painfully slow) then tried Lubuntu and couldn't even get it to install.  I was going to give away that PC, but couldn't find a usable distro to run on it.

But back to the future, if a GUI doesn't add functionality or make things easier, it's not worth upgrading.  I'll stick with Unity for a little while and see if it's acceptable.  So far, it's quite a learning curve, and it does seem slower, even on a 2.6 MHz quad-core with 6 GB, although I don't have a fast gaming video card - just a 9500GT.  So Unity feels a bit sluggish even compared to Aero!  Unity 2D uses 99% of my Athlon 200 MHz file server just running System Monitor and one Nautilus window.  I don't recall Gnome 2? in Ubuntu 11.04 on that PC using more than 44% CPU with just those two apps running.

---

### Post by coffeecat on 2011-10-16
> **SkyeFerret said:**
> Keep discussing if you want.

Nope - this is a support area, not a debate area of the forum.

@OP, if you need help with any aspect of the 11.10 gnome-session-fallback desktop, or any other desktop you may choose, please start a new thread. Ditto anyone else. If anyone wishes to debate the relative merits of the available desktops, there are areas in the forum for this, but please do so in accordance with the forum Code of Conduct.

Thread closed.

---

