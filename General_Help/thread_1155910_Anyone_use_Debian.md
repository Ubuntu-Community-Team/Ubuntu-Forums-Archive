---
title: "Anyone use Debian?"
date: 2009-05-11
forum: General Help
---

### Post by chrispche on 2009-05-11
I want to try Debian and naturally stepping from Ubuntu to Debian is the way to go.

I would like the help with the following.

How do I install w32codecs, DVD playback. The ability to install all codecs (mp3's, mp4's etc). A repository for Skype GoogleEarth etc. Also how do you install macromedia flash plugin.

Also I went to use Gnome and compiz fusion, so some info on getting my nVidia Geforce FX card would be nice.

Thank you.

Are all these things in the repos? Or do I have to install a third party repo?

Again thanks in advanced for the help.

---

### Post by skymera on 2009-05-11
I used Debian Testing (Squeeze) a few months back.

It was "ok". Not as simple to use as Ubuntu, nor any more customisable which was a shame.

You need to install your Nvidia driver manually and create the kernel modules manually. That's what i did with my ATi.

I didn't fancy that so i changed back to 9.04 :)

---

### Post by m_duck on 2009-05-11
For codecs and DVD playback you will want to add the  [debian multimedia](http://debian-multimedia.org/) repo. You will also want to add "non-free" and "contrib" to all the standard repos to open up some extra stuff. For graphics, I've only used nVidia drivers, but their wiki has a step-by-step guide for getting them installed.

With regards to skype and google earth, I have no idea as I don't use them.

HTH

---

### Post by Wiebelhaus on 2009-05-11
Both of the users above me are correct.

---

### Post by snowpine on 2009-05-11
I think Ubuntu would be perfect for you needs; I would not recommend switching to Debian in your case. You would be wasting a lot of time making Debian exactly like Ubuntu. :)

---

### Post by chrispche on 2009-05-11
I agree. Sticking with Ubuntu.

---

### Post by Lampi on 2009-05-11
You find skype for Debian on their website: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

I use Ubuntu and Debian/Stable, Ubuntu is great as a client system, Lenny is the perfect choice for a server system.

GoogleEarth - don't know, the flash plugin is the same on Debian and Ubuntu, just install flashplugin-nonfree or gnash

---

### Post by snowpine on 2009-05-11
If you do decide to switch to Debian, the smxi script ([www.smxi.org](www.smxi.org)) makes it really easy to install nonfree apps like skype, opera, google earth, flash plugin, etc.

---

### Post by chrispche on 2009-05-11
Thanks that helps. I might just try Debian now.

---

### Post by kerry_s on 2009-05-11
i'm just now doing a fresh debian testing base build up.

grab the net installer you can install everything with it:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

it will do all 4 desktops, server or what ever you want. i uncheck everything to just get a base install, then add what i want from there.

---

### Post by T.J. on 2009-05-19
I do quite a bit. I'm going to play "devil's advocate" here a little bit, since everyone seems to fall on the side of the fence for Ubuntu.  No flame wars intended, but Debian deserves a little credit too.

As everyone here knows, Ubuntu is a patched version of Debian "unstable" tree. I admit that Ubuntu has some nice useability features over Debian, but Ubuntu's strengths are also its weakness. It's much harder to tailor than Debian.  My point is that each release of Ubuntu,  each release is moving so far in the direction of a "user friendly" that a number of vital features that long standing users have come to expect are not really usable in Ubuntu.

One thing I can't fathom, for example is Ubuntu's refusal to support volume management out of the box. (Yes, I know it is on the "alternate installer", but the alternate discs are really hit or miss at best.  I've found them to be very buggy, even worthless.) 

Multimedia in Intrepid was a bit of a pain.  Some of the dependencies on GStreamer were all messed up, and I found at least one codec that I know was bugged, because a number of older MP3's would not play properly, depending on your installation. It was a known issue (I looked), but no one had any idea what was going on. I had to trace it down and patch the system myself.  I understand why things are as they are, but a bit more testing of the packages outside of the core system would be nice. 

These are just two examples. I'm not saying that Debian doesn't have quirks, either.  It's just that some of the really annoying bugs in Ubuntu are fixed in Debian and vice-versa.  It's a shame that they can't work together better, but the communities are very different.  Ubuntu uses a board, where Debian still uses mailing lists, for example.  Ubuntu has great enthusiasm and energy, while Debian has the technical focus.

---

### Post by ashmew2 on 2009-05-19
Well i think the basic aim of Ubuntu was making Debian better in every way possible..So i think that if you really want to feel the breeze , go for a completely different family/things..like if you are running Ubuntu with Gnome , Try Gentoo/Sabayon with FluxBox or Fedora with XFCE/ICE/KDE :D

---

### Post by ashmew2 on 2009-05-19
> **T.J. said:**
> 

One thing I can't fathom, for example is Ubuntu's refusal to support volume management out of the box. (Yes, I know it is on the "alternate installer", but the alternate discs are really hit or miss at best.  I've found them to be very buggy, even worthless.) 



I beg to differ regarding the Alternate Discs...They've served me well enough when the LiveCDs failed me one after the other.

---

