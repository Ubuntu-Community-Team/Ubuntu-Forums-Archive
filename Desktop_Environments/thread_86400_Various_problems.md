---
title: "Various problems"
date: 2005-11-05
forum: Desktop Environments
---

### Post by stalflare on 2005-11-05
Hi everyone...

I am new to linux and Ubuntu, so maybe some of the questions here below will be a bit basic...

I have installed Ubuntu on my laptop, a P3 1.0gh, 320Mb Ram, hd 10gb. It works all fine, but I seem to have problems with nautilus NOT opening directories every now and then, or taking a great deal of time in doing so.

I am also experiencing a very slow internet pages load time. It's strange to see that on Windows pages seem to load up in a second and it takes longer for Ubuntu... The connection is the same, as well as the browser (firefox)... Has anyone experienced these sorts of problems?

Last, I am trying to copy a 4,2 gig file from the main HD to a USB external drive, but when it reaches 4 gigs it doesn't finish the copy and stops... It's not a problem of space, as there is in aboundance (more than 10 gigs).. what could it be?

Thanks a lot for the help!

---

### Post by aysiu on 2005-11-05
May I suggest a few fixes? Well, they're not exactly fixes. They're more like workarounds.

First of all, consider using XFCE. It's an almost fully-featured desktop environment that's extremely lightweight and fast. I've never had any freeze-ups or problems in XFCE (occasionally I have in Gnome or KDE, though). Also, even though you have over 256 MB of RAM, Gnome may not be at its optimum with the amount of RAM you have.

The other thing to consider is using Firefox 1.5 instead of the regular Firefox. You could also try using the FasterFox extension, too. Yeah, I know--that still doesn't explain why the same browser would be slower on the same connection. I don't know why that's happening (Firefox is actually faster on my Ubuntu installation than my Windows one).

---

### Post by stalflare on 2005-11-05
Hi aysiu!!

Thanks for the reply... How do I set up XFCE instead of Nautilus? I am sorry to ask such simple questions but I am really a newbie...

I have tried looking at the package manager, but I have found little evidence of XFCE there, plus once I install it how do I tell Ubuntu to use it instead of Nautilius?

Af for firefox, I'll try installing 1.5, that should be easier! :)

Thanks a lot!

---

### Post by aysiu on 2005-11-05
[QUOTE=stalflare]Hi aysiu!!

Thanks for the reply... How do I set up XFCE instead of Nautilus? I am sorry to ask such simple questions but I am really a newbie...

I have tried looking at the package manager, but I have found little evidence of XFCE there, plus once I install it how do I tell Ubuntu to use it instead of Nautilius?[/quote] Well, it's not really instead of Nautilus. Nautilus is the file manager for Gnome (the desktop environment). XFCE is another desktop environment that has its own file manager (called Rox-filer).

You have to [enable extra repositories](http://www.psychocats.net/linux/sources.php) to get XFCE. Once you do that go to Synaptic and check off XFCE4 and a bunch of other XFCE-related things (whatever you think might be useful).

To use XFCE, you log out of Gnome. Then, before you log in again, go to "Session" and select XFCE for your session.

> 
Af for firefox, I'll try installing 1.5, that should be easier! :)

Thanks a lot! It may actually not be easier. Installing the [FasterFox extension](https://addons.mozilla.org/extensions/moreinfo.php?id=1269&application=firefox) is probably easier. If that's not suitable as a solution, you can [install 1.5](https://wiki.ubuntu.com/FirefoxNewVersion).

---

