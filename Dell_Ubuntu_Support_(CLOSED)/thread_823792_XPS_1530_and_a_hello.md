---
title: "XPS 1530 and a hello"
date: 2008-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by NMbottlecap on 2008-06-09
Hey all I have decided that I've had it with Mac, Windows, and am going Ubuntu fully, I've played with it before and enjoyed it, but I'm getting fed up with being told how I can use my OS.  It's mine dangit!  So I ordered an XPS 1530 and a DVD from Ubuntu and they should be getting here about the same time.  I can't wait to blow away Vista, and install Ubuntu.  \\:D/

Are there any gotchas in regards to the installing that I should be aware of?

---

### Post by veedub on 2008-06-09
If you install hardy, you will need to download and install the beta NVIDIA drivers.  Wireless (intel 3945abg) works great!(the most seamless wireless on a linux distro).  However, these two main bugs will require your patience:

1:   Standby doesn't seem to work very well.  Very loud beeps upon resume, and you get either a black or white screen.  However, blindly entering your password works, and hopefully you don't need to resume when people are sleeping.

2:   Firefox is slow as molasses when viewing sites containing flash and/or java (especially java).  Don't know if this is firefox related, but it sucks nonetheless.

I haven't been able to fix them and it's driving me nuts!

Also, 

You _may_ need to install new alsa drivers to get your mic working.  First try unmuting your digital input device.

The biometric fingerprint reader doesn't work.  But then again, maybe it does, it is not important to me.

Do NOT use your media direct buttons.  You will mess up your partition table.

It takes some work, but once setup it's nice.  I did find that all of the stuff that doesn't work in hardy (8.04) worked great in gutsy(7.10) EXCEPT for wireless.  However, wireless is seamless in hardy, and everything else needs work.  Mainly the graphics, but that is because hardy uses a newer kernel that is incompatible with the version 169 on some nvidia cards including the 8600GT that is in my XPS1530 ...

---

### Post by sc00ter on 2008-06-10
My advice is, do your research first and be sure you've got a standby machine with working internet just in case you need to look something up (if you encounter any issues like network etc.).

These two links helped me a great deal with my install on the m1530:

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530) (Gutsy + Hardy)

and:

[http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530) (Hardy)

My experience was very positive as I didn't go into the whole process blind, I'm very happy with Hardy on the M1530, most things worked out of the box, with very little tweaking.

---

### Post by LK_gandalf_ on 2008-06-11
I disagree with what has been said over.
I have a Dell xps M1530, I've installed Kubuntu hardy 64 bit and I have no problems with nvidia card, standby-mode, microphone, slow firefox.

Everythings works out of the box, except:
- touchpad (you have to follow a quick step to fix it)
- minor problem to keyboard (same fix of touchpad works)

Enjoy your Dell :popcorn:

---

