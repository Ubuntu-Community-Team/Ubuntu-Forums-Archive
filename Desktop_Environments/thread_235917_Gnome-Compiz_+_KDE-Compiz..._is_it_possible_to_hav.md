---
title: "Gnome-Compiz + KDE-Compiz... is it possible to have both?"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Fyda on 2006-08-13
Okay, so maybe I'm really pushing my luck here - and this seems so frivolous of me, sorry - but, here goes anyway.

After following the [Compiz forum tutorial](http://www.compiz.net/viewtopic.php?id=389) (the second method - creating a separate Xgl session to load Compiz, while retaining the original Gnome session), I now have a **Gnome** session and an **Xgl** session. After this, I installed the *kubuntu-desktop* package, giving me an additional **KDE** session.

I am wondering if it'd be possible to install Compiz again in such a way that I will have a sessions list like this:

- Gnome
- Xgl (on Gnome)
- KDE
- Xgl (on KDE)

Because of the existing Xgl session, I have the *compiz-gnome* package installed. When I attempt to install *compiz-kde*, it refuses and tells me that installation would break something else.

This may be asking a bit much, but would it be possible to have Compiz enabled for *both* WMs, instead of just one or the other?

(See, I said this was a frivolous request... :oops: )

---

### Post by BitTorrentBuddha on 2006-08-13
Not unless you downgrade to compiz and compiz-gnome quinn28, there aren't that many major improvements in quinn29 so it's not a big deal, just download and install [these packages](http://www.beerorkid.com/compiz/archives/quinndebs-compiz_0.0.13-0quinn28.tar.gz), and answer yes to anything involving downgrade. When quinn29 KDE debs are released onto the repo you'll get an upgrade alert for all three.

---

### Post by Fyda on 2006-08-14
Thank you! It works, and I now have a Xgl-KDE session. :D

I'm wondering, though... I followed [Frodon's tutorial](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29) (as an alternative to [this thread](http://www.ubuntuforums.org/showthread.php?t=174233)), which is how I got it to work. But neither of those ever made mention of the *compiz-kde* package! I wonder if the downgrade to quinn28 was necessary after all... or are both the Gnome and KDE sessions running off the Gnome files? (In other words, is *compiz-kde* and the downgrade method even necessary?)

Also, one significant tradeoff I had to make to use the downgraded packages: I can now no longer install *cgwd* and *cgwd-themes*, because I effectively broke their dependencies.

If it turns out the downgrade wasn't necessary, then I guess I should reinstall the latest packages and get those fancy window borders back. :S Eh, I'll test it later. Thanks for your help!

(By the way, the latest version is Quinn31...)

---

### Post by BitTorrentBuddha on 2006-08-14
Compiz-kde and compiz-gnome quinn28 both depend upon compiz quinn28. Once compiz-kde quinn29 is released then you can re-upgrade both compiz and compiz-gnome to quinn29. However, I'm using quinn28 right now and I have cgwd installed... Have you tried reinstalling without compiz quinn29 installed? (I'm not a fan of the menu shadowing though, if you could help me back and lead me to a way to turn that off.)

---

### Post by Fyda on 2006-08-14
> **BitTorrentBuddha said:**
> (I'm not a fan of the menu shadowing though, if you could help me back and lead me to a way to turn that off.)

Hmm. It appears that the menu shadows use the same settings as the window frame shadows. So, setting their radius to 0 in CGWD (under the *Edit* tab) removes *both*. (But, maybe you already tried this and were not satisfied with the results?) I'm not a l33t haxor or anything, so I don't know how one would go into the code to manually alter *only* the menu shadow settings. Sorry...

Anyway, I decided I'd experiment and see what happens when I upgrade as the package manager requests (upgrade *compiz* and *compiz-gnome*, remove *compiz-kde*), install *cgwd* and *cgwd-themes*, then try to load the Xgl-KDE session. I'm sure it won't work at all, but I have to be absolutely sure.

---

### Post by Fyda on 2006-08-14
:O What... the... !?!

Erm, the Xgl-KDE session is running with Compiz enabled, **without** *compiz-kde*.

Naturally, CGWD works, too...

I'm half-bewildered, half-unsurprised. I guess the tutorials had me running Compiz in KDE using the Gnome resources after all...

Weird.

---

### Post by BitTorrentBuddha on 2006-08-14
That is strange, I was always under the assumption that Compiz-KDE was required to run compiz under KDE.

---

