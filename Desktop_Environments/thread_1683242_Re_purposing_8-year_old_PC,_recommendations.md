---
title: "Re purposing 8-year old PC, recommendations?"
date: 2011-02-07
forum: Desktop Environments
---

### Post by ShadowPuppet on 2011-02-07
Re purposing 8-year old PC, recommendations on what desktop environment. 

Bit of a newbie to the scene, but I've been tinkering for a while with Ubuntu/linux.

The machine is an AMD AthlonXP 2700+ with 1.5GB of memory and an nvidia 6600GT. I have Ubuntu 10.04 on it right now with the standard gnome environment that came with it, but it is slow and terribly laggy. 

I was looking at XFCE and LXDE. I know either would work, was looking for pros/cons, ect.

Thanks!

---

### Post by 3Miro on 2011-02-07
XFCE - fully featured, basically faster Gnome. Personally, it is my favorite.

LXDE - lighter than XFCE, but missing some features and still somewhat buggy at times. LXDE is the only environment that gives good performance on an external monitor with my crappy laptop.

I would try XFCE, if this doesn't work, try LXDE.

---

### Post by ajgreeny on 2011-02-07
> **ShadowPuppet said:**
> Re purposing 8-year old PC, recommendations on what desktop environment. 

Bit of a newbie to the scene, but I've been tinkering for a while with Ubuntu/linux.

The machine is an AMD AthlonXP 2700+ with 1.5GB of memory and an nvidia 6600GT. I have Ubuntu 10.04 on it right now with the standard gnome environment that came with it, but it is slow and terribly laggy. 

I was looking at XFCE and LXDE. I know either would work, was looking for pros/cons, ect.

Thanks!
Crikey!  That's not what I would think of as very old, nor should it be too slow.  I have 10.10 standard ubuntu on an Acer Travelmate with Celeron 2.6GHz and just 512 MB ram, and whilst not fast, it is still very usable, and a lot better than the XP it came with.  have you checked that the startup applications are not robbing you of resources?

I am sure there must be ways of using ubuntu on that machine without it being too slow.

---

### Post by elementunkn on 2011-02-07
I've installed Ubuntu on slower machines than yours and it was still very useable. Maybe try 10.04 or another distro just to see if it gets any better.

---

### Post by mcduck on 2011-02-07
You call that slow? :D

I have 10.10 running on a 450MHz K6-2 with 128MB of RAM. And that's completely usable, although browsing the web pretty much *requires* using adblock and not bothering to even try to install Flash. :D

Anyway,XFCE is only a bit lighter than Gnome is, and you can pretty much make the difference negligible with a few gconf tweaks in Gnome. So if you feel Gnome is to slow for you, you probably want something much lighter.

I'd personally recommend just using a minimal install of Ubuntu, an Openbox as the window manager. Although if you don't feel like hand-configuring your setup and want something easier, perhaps a minimal install+LXDE would do the trick (LXDE is pretty much Openbox + some desktop environment-style stuff like session manager, panel and graphical configuration tools). Or you could try [CrunchBang]("http://crunchbanglinux.org/"), which would give you a decent Openbox configuration out-of-the-box... ;)

---

### Post by ShadowPuppet on 2011-02-08
Forgot to mention that it is running 10.04.

It was my main machine all the way up until the summer of 08, so its got some senemental value, and I wouldn't call it "slow," it's just running slow.

There aren't really any processes hogging up too many resources, but the CPU is pegged at nearly 100% with just having a web browser open (no flash heavy sites, Adblock already in use), or just other, not-intensive, programs open. 

I know that a clean reinstall is probably a knee-jerk long-time Windows-user kind of thing, but I'll do some more poking around after classes/work today. 

Thanks!

---

### Post by cascade9 on 2011-02-08
> **mcduck said:**
> Anyway,XFCE is only a bit lighter than Gnome is, and you can pretty much make the difference negligible with a few gconf tweaks in Gnome. So if you feel Gnome is to slow for you, you probably want something much lighter.

Isnt ubuntu @ stock settings a lot 'heavier' than even gnome-core on a minimal install? 

> **mcduck said:**
> I'd personally recommend just using a minimal install of Ubuntu, an Openbox as the window manager. Although if you don't feel like hand-configuring your setup and want something easier, perhaps a minimal install+LXDE would do the trick (LXDE is pretty much Openbox + some desktop environment-style stuff like session manager, panel and graphical configuration tools). Or you could try [CrunchBang]("http://crunchbanglinux.org/"), which would give you a decent Openbox configuration out-of-the-box... ;)

Openbox on 1.5GB, 6600GT, 2700+? Sure, if you like openbox. I dont like it much myself. 

I run Xfce4 on systems with similar spec to that, and installing lxde (or openbox) doesnt seem to make the system any more snappy than with Xfce4. 

@ ShadowPuppet- If you dont want to spend time cleaning out uneeded prorams, etc from ubuntu, and you dont want to haev to reinstall, then I'd try xfce4 and/or lxde (or even openbox LOL). Easier than reinstalling, and you can get a feel for xfce/lxde.

---

### Post by DMGrier on 2011-02-08
I would check how you have it set up cause Ubuntu 32 bit Os should run just fine on that, you do have 32 bit installed, not 64 bit right?

---

### Post by snowpine on 2011-02-08
Have you installed the correct drivers for your Nvidia card?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by cascade9 on 2011-02-08
> **DMGrier said:**
> I would check how you have it set up cause Ubuntu 32 bit Os should run just fine on that, you do have 32 bit installed, not 64 bit right?

64bit/32bit doesnt make that much difference. If anything 64bit would be slightly faster, though it might use a bit more RAM (with 1.5GB thats not really an issue)

Not that ShadowPuppet can run 64bit anyway, AthlonXPs are 32bit only.

---

### Post by ajgreeny on 2011-02-08
> **ShadowPuppet said:**
> Forgot to mention that it is running 10.04.

It was my main machine all the way up until the summer of 08, so its got some senemental value, and I wouldn't call it "slow," it's just running slow.

There aren't really any processes hogging up too many resources, but the CPU is pegged at nearly 100% with just having a web browser open (no flash heavy sites, Adblock already in use), or just other, not-intensive, programs open. 

I know that a clean reinstall is probably a knee-jerk long-time Windows-user kind of thing, but I'll do some more poking around after classes/work today. 

Thanks!
If the cpu is running at close to 100% with just a web browser open, there is definitely something going wrong somewhere.

Open up ```
top
``` in terminal, hit upper case P, and see what is using all your cpu.

---

