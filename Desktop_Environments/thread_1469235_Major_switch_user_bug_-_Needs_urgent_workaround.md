---
title: "Major switch user bug - Needs urgent workaround"
date: 2010-05-02
forum: Desktop Environments
---

### Post by keech on 2010-05-02
I am running 10.04 .....when you use switch user and try to switch back from another user you get a blank screen ...the system freezes...need to physically reboot. One more thing, when you switch user using 'Switch from *username*'and try to login back without going to any other user, the screen just freezes in the login screen. I am not sure why this happening, I have tried the following but did'nt work. 

Uninstalled gnome-screensaver
deleted the user,created new

There are several bug lists in this regard.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/546578]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/546578")

Someone needs to find a workaround else...its going to make people regret opting for Ubuntu

---

### Post by 3rdalbum on 2010-05-02
The problem is almost certainly your rubber-band graphics card. I had a similar ATI card and was always having that problem. You don't get it with Nvidia cards.

---

### Post by keech on 2010-05-02
I found a work around...if you lock the screen and switch users the problem is not occurring... so I feel it is sure some thing to do with the switch user appelate

---

### Post by mrtoolate on 2010-05-02
when you use switch user and try to switch back from another user you  get a blank screen


same problem my desktop i upgrade to 10.4 and my laptop install fresh 10.4

---

### Post by Multi_User on 2010-05-02
I have the same problem on my Eee box with integrated Nvidia graphics. And I did not install the special proprietary Nvidia driver because it caused problems with my networking.

---

### Post by keech on 2010-05-06
It is pity no one is there to help me out...it is the real state of Ubuntu...after stripping of the hype

---

### Post by pleasecallmejames on 2010-05-07
Try turning off Visual Effects

  System > Preferences > Appearance > Visual Effects > None

I am testing Lucid in a VirtualBox virtual machine and have the problem when Visual Effects are on but not when they are off.  I will not upgrade from Karmic until this bug is fixed.

---

### Post by isaacd on 2010-07-23
I am having a similar problem with an IBM Thinkpad running ubuntu 10.04. I would not be surprised if it had a bad graphics card, but I don't know. Visual effects are turned of, and the problem still persists. It also persists when I lock the screen and switch users from there. I know that when I boot up, the ubuntu logo has funny green lines around it, but once it is done loading, and all the dots are solid red, the green lines go away, and the mouse pointer appears.

When I try to switch users, I see about half of the purple screen you get on bootup with the ubuntu logo and dots below it. The mouse pointer is there and movable, and I hear the bongos announcing my arrival to the login screen, but nothing appears on my screen.

If this is not possible to fix, is it possible to remove the switch user option?

---

### Post by isaacd on 2010-07-23
Ha, it works now. Don't know what changed...

---

### Post by keithspg on 2010-07-23
> **3rdalbum said:**
> The problem is almost certainly your rubber-band graphics card. I had a similar ATI card and was always having that problem. You don't get it with Nvidia cards.

wrong! I get this and have had this since I installed Lucid. Was not a problem in Karmic. It is a major bug IMO and should be treated as such. 

I am running an nvidia card and the nvidia driver. I get it with no effects or with minimal.

KeithG

---

### Post by WinRiddance on 2010-07-24
> **3rdalbum said:**
> The problem is almost certainly your rubber-band graphics card. I had a similar ATI card and was always having that problem. You don't get it with Nvidia cards.

Yeah, that's what I thought too ... until my Son did his upgrade to 10.04 and he happens to have a newer system with a Nvidea chip. After the upgrade he ket getting a repeating login screen that would let him log in, then loop right back to the login screen ... endlessly. That too is a reported bug in 3 different flavors, affecting all versions of Ubuntu. Although it only took us about an hour to find a fix and apply it, it certainly is the kind of thing that frightens people away from Ubuntu.

---

### Post by ac7ss on 2010-08-03
I have this trouble as well. Apparently nobody has a solution for it. (The only way I can even shut down the machine is to SSH from another computer and issue a restart now command.)

I also recently lost my virtual terminals at the same time.

Running GDM as my login.

```
           *-display
                description: VGA compatible controller
                product: Radeon 3100 Graphics
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff(prefetchable) ioport:d000(size=256) memory:fbef0000-fbefffff memory:fbd00000-fbdfffff

```

---

