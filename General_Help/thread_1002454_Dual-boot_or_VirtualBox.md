---
title: "Dual-boot or VirtualBox"
date: 2008-12-05
forum: General Help
---

### Post by happinesskills on 2008-12-05
I have a Dual-Boot with Ubuntu Hardy & Windows Vista. After about 6 months with Ubuntu, I have grown to love it, & I want to get rid of Vista ENTIRELY. I hate Vista. What I want to know is whether or not I should continue to Dual-Boot the two, or to download VirtualBox & install Windows XP on it ( I will get the WinXP disc from my cousin).

The only reason I am keeping Vista is because I need it to run a few apps. Particularly Flash CS4, iTunes, & Samsung PC Studio for my phone. If you could help me decide, or if you can get me a replacement for these, that would be great. Please note: I have already tried Wine, but it doesn't work well with these apps

---

### Post by Nathan Sweeney on 2008-12-05
There will be a performance hit when running a virtual machine.  What are your specs?

The only app that performance would make a difference that I see is Flash.  What do you use Flash to accomplish.  I found [Synfig]("http://www.synfig.org/Main_Page") that appears to do 2d animations.  I don't know anything about it though.

---

### Post by mhh91 on 2008-12-05
why do you need the Samsung PC studio?

i think you can transfer files from and to the phone seamlessly on ubuntu

---

### Post by jespdj on 2008-12-05
> **happinesskills said:**
> The only reason I am keeping Vista is because I need it to run a few apps. Particularly Flash CS4, iTunes, & Samsung PC Studio for my phone. If you could help me decide, or if you can get me a replacement for these, that would be great. Please note: I have already tried Wine, but it doesn't work well with these apps
When you run Windows in a VirtualBox virtual machine, then it won't be able to make use of the full power of your graphics card. VirtualBox presents a virtual video card to the operating system running inside the virtual machine, and unfortunately that virtual video card does not support accelerated 3D graphics. So, for example games that need the 3D graphics capabilities will not run well in VirtualBox.

However, for the applications that you mention I think it's no problem. I've used Photoshop CS3 on Windows XP in a virtual machine and it isn't noticeably slower than on "native" Windows.

---

### Post by TeXtonyx on 2008-12-05
If this is a desktop, I would add a second drive, a used 80GB is
about $20. I think XP Pro and another linux OS could go on the
second drive and you could delete Vista if you wanted, or shrink
it, that is one good feature, it comes with a partition resizer.

Or you can put a backup on the second drive. If you have only one
OS installed on one drive then its sneakernet time if that system
goes down. A second OS means you can use email and the internet
to find solutions for not-able-to-boot problems for the other OS.

---

### Post by happinesskills on 2008-12-05
This will answer all your questions

specs - 2 x 1.73 GHZ processor - 1GB RAM - 160GB Hard Drive - It's a Toshiba Satellit A200 PSA-F3A (it's a laptop)

I use flash to make animations. I looked at Synfig, but It looks very confusing compared to flash CS4, & I found out that it doesn't export as SWF, which is what I mainly need it for. I have uploaded a few things to Newgrounds.com.

I use Samsung PC Studio to put stuff on my phone, I haven't tried pluggin it into ubuntu yet, but I'll give it a go after I've finished in Vista. I don't like rebooting into Vista because it takes at least 10 minutes before it gets to normal speed & I can start using it (now you can see why I want to change to ubuntu).

I (surprisingly) don't play a lot of games, so 3D graphics aren't really a problem. Is there  way to configure VirtualBox to use my actual Video card (which I found out is pretty good)?

And yes I have a laptop

---

### Post by happinesskills on 2008-12-06
Samsung PC Studio problem's solved! After finishing up in Vista, I went into Ubuntu & plugged my phone in. It worked! Now I can delete the shitty stuff that came pre-installed on the phone that I couldn't delete on the phone or through Samsung PC Studio! Yay!

---

