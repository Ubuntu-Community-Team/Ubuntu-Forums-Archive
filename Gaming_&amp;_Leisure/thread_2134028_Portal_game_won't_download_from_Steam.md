---
title: "Portal game won't download from Steam"
date: 2013-04-09
forum: Gaming &amp; Leisure
---

### Post by Dallas2coolio on 2013-04-09
Does anyone know a way so I can download Portal from Steam? Since I got the game last year but when I downloaded the Steam program for Linux and tried to install but it says the game is not for this platform and I can't even download it. I thought with Wine it would work fine. How can I download the full game I got from Steam?   Thanks

---

### Post by myromance123 on 2013-04-10
You would need to install Steam inside Wine, so that it thinks its inside Windows. That way, you can download your Windows games and play them. The Windows Steam client is a separate entity from the Linux Steam client.

The easiest way to use Wine and still be free is PlayOnLinux. Get it here:
[http://www.playonlinux.com/en/download.html]("http://www.playonlinux.com/en/download.html")

Once you have POL installed, click the big Install button. In the search bar, just type Steam. It will appear in the list, select it and click Install. Then just follow the instructions, and you should have Steam installed inside Wine without a problem.

I hope this answers your question.

P.S: Linux Steam cannot download Windows versions of your games, to put it simply.

---

### Post by Dallas2coolio on 2013-04-10
Is Wine better to use ot PlayOnLinux better? I been using Wine and the latest version but should I use PlayOnLinux instead?

---

### Post by myromance123 on 2013-04-10
PlayOnLinux uses Wine. It makes it easier to try many different versions of Wine, whether bleeding edge new or even old versions.

In my opinion, it is definitely better to use PlayOnLinux. It takes a while to learn, but it makes handling Wine a lot easier and cleaner. Give it a shot. If you've been using the standalone Wine this entire time, you'll find that PlayOnLinux is a breeze in comparison.

---

### Post by VeeDubb on 2013-04-10
A side note, I wouldn't just install steam through playonlinux.

What you'll find, is that MANY games that play fine using wine, each require slightly different tweaks and adjustments to wine to make them work properly, and that can be a real headache.  POL is designed to address that by setting each one up in it's own instance of wine, even installing different wine versions if a program requires a specific version to work.

So, instead of just installing Steam, tell POL that you want to install portal.  Early in the installation process it will ask if you're using a disc or the Steam Store version.  Tell it you want to use steam, and it will walk you through not only installing steam, but also installing portal with all of the tweaks to run it perfectly (or as close to perfect as you can get).  It then keeps that instance of steam segregated from everything else, so that when you want to install something like Skyrim through steam, which requires a completely different set of tweaks and settings to play well, you can keep the two completely separate and clean.

---

### Post by oldrocker99 on 2013-04-10
> **VeeDubb said:**
> A side note, I wouldn't just install steam through playonlinux.

What you'll find, is that MANY games that play fine using wine, each require slightly different tweaks and adjustments to wine to make them work properly, and that can be a real headache.  POL is designed to address that by setting each one up in it's own instance of wine, even installing different wine versions if a program requires a specific version to work.

So, instead of just installing Steam, tell POL that you want to install portal.  Early in the installation process it will ask if you're using a disc or the Steam Store version.  Tell it you want to use steam, and it will walk you through not only installing steam, but also installing portal with all of the tweaks to run it perfectly (or as close to perfect as you can get).  It then keeps that instance of steam segregated from everything else, so that when you want to install something like Skyrim through steam, which requires a completely different set of tweaks and settings to play well, you can keep the two completely separate and clean.

By golly, five years of using wine and PlayOnLinux, and I never thought to just tell POL to install, oh, Skyrim. I did and, yes, POL asked me whether it was from disk of from Steam, and it's downloading now.

Patience, I tell myself...


,,,and it was rewarded! Skyrim runs just as well under PoL as it did on my soon-to-be-discarded Win7 partition!

---

### Post by VeeDubb on 2013-04-11
> **oldrocker99 said:**
> ,,,and it was rewarded! Skyrim runs just as well under PoL as it did on my soon-to-be-discarded Win7 partition!

If you think that's impressive, log out of Unity, and log back in to Gnome Failsafe (no effects), then try Skyrim again.  On my system the difference is pretty huge.

---

### Post by oldrocker99 on 2013-04-11
Uh, I don't use Unity; this was using MATE 1.42. I imagine that LXDE, XCFE, or even KDE with desktop effects disabled for full-screen windows would do better than Unity. I'm not crazy about the current state of GNOME, either.

---

### Post by VeeDubb on 2013-04-12
> **oldrocker99 said:**
> Uh, I don't use Unity; this was using MATE 1.42. I imagine that LXDE, XCFE, or even KDE with desktop effects disabled for full-screen windows would do better than Unity. I'm not crazy about the current state of GNOME, either.

Fair enough.  Personally, I'm extremely happy with Unity, all except for it's poor performance with full screen games.  Unredirect fullscreen helps, but really isn't a perfect solution.  In any case, I suppose that's probably for a different thread.

---

