---
title: "Mini 9 Yahoo Junk"
date: 2009-03-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cowchip7 on 2009-03-26
Is there a way to take off the yahoo bloatware in one fell swoop? I thought I could avoid this with a Linux system. Thanks Dell!

---

### Post by anjilslaire on 2009-03-26
I've switched to 8.10, but I do know its removeable. Open Synaptic and look for yahoo or toolbar.

Otherwise someone will be along shortly to give specifics.

---

### Post by Cowchip7 on 2009-03-26
Yeah. I'm thinking about switching to 8.10 as well. But I would rather wait until there is better support for the intel atom architecture. Maybe this fall with Jaunty?

---

### Post by anjilslaire on 2009-03-26
8.10 works perfectly in the regular x86 architecture on the mini 9, just so you know :)

---

### Post by Cowchip7 on 2009-03-26
> **anjilslaire said:**
> 8.10 works perfectly in the regular x86 architecture on the mini 9, just so you know :)

So I've read. It only requires a minor tweak for the sound. However, I also heard it slightly reduces battery life and speed. Any thoughts?

---

### Post by anjilslaire on 2009-03-26
I get about 3:55 on a full charge, and don't really notice any speed issues. I've upgraded the bios to A04, and installed 2gigs of ram. It's certainly speedy enough.

---

### Post by Cowchip7 on 2009-03-26
> **anjilslaire said:**
> I get about 3:55 on a full charge, and don't really notice any speed issues. I've upgraded the bios to A04, and installed 2gigs of ram. It's certainly speedy enough.

You're tempting me...

---

### Post by lswartz on 2009-03-26
> **anjilslaire said:**
> I've switched to 8.10, but I do know its removeable. Open Synaptic and look for yahoo or toolbar.

Otherwise someone will be along shortly to give specifics.

I turned mine off on Firefox. You mean I have to go looking for more to delete:(.

---

### Post by jaqrah on 2009-03-26
As an aside, I wrote a very enthusiastic review for the Dell Mini 9 on the Dell site.  The only con I had was the despicable yahoo toolbar.  Dell never allowed it to be published.  Hmmm...wonder why? ;)

---

### Post by Ryback on 2009-03-27
Lets have the review here!  Don't let them stifle your freedom :)

---

### Post by Cowchip7 on 2009-03-27
> **Ryback said:**
> Lets have the review here!  Don't let them stifle your freedom :)

Hear, Hear. Post that son of a gun here.

I will be trying out this Dellbuntu version. If there is one thing I can't stand I might go 8.10 with remix.

---

### Post by Talon2 on 2009-03-27
> **Cowchip7 said:**
> So I've read. It only requires a minor tweak for the sound. However, I also heard it slightly reduces battery life and speed. Any thoughts?

If 8.10 reduced the battery life and speed it isn't to the degree that I have noticed it.  I stayed with the factory pre-install until I could not stand the problems any more.  I did a clean install of 8.10.  Wow.  Much better.  I consider that Dell 8.04 pre-install Alpha level stuff.

---

### Post by anjilslaire on 2009-03-27
I believe [upgrading the bios]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=INSPIRON910&os=WW1&osl=en&catid=&impid=") improves boot time and battery life, too:
> 
Fixes and Enhancements
Dell Inc.
Copyright (C) 2009, All Rights reserved.
[www.dell.com](www.dell.com)

Systems: Dell Inspiron 910
Version: A04
Build Date: 01/05/2009

=========================================================
1.Resolve the error message can't show after setting supervisor password and then using asset.com to delete service tag.
2.Resolve rotation setting with external LCD after resume from S3
3.Computrace support.
4.Display switch (Fn+8) on DOS mode (LCD ->CRT ->LCD )
5.Desktop icon position can't be fixed after PC re-boot
6.Display can't keep on extend mode after press Fn+8 to switch.
**7.Battery performance improvement.**


---

### Post by ugm6hr on 2009-03-28
> **Cowchip7 said:**
> Is there a way to take off the yahoo bloatware in one fell swoop? I thought I could avoid this with a Linux system. Thanks Dell!

Yes.

```
sudo apt-get remove yahoo-toolbar-extension
```

Or "uninstall" yahoo-toolbar-extension from Synaptic Package Manager.

PS: I believe BIOS updates are not officially supported with Ubuntu.

---

