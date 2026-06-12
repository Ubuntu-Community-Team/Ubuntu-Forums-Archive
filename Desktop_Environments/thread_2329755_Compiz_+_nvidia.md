---
title: "Compiz + nvidia"
date: 2016-07-04
forum: Desktop Environments
---

### Post by Plasma_NZ on 2016-07-04
Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid
3.19.0-64-generic
Compiz 0.9.12.1
NVIDIA-Linux-x86_64-367.27

[[img]http://iforce.co.nz/i/lxrk50l1.5da.png[/img]](http://www.iforce.co.nz/View.aspx?i=lxrk50l1.5da.png)



Use expo plugin ...

When i drag something around on the screen, it doesn't seem to refresh as you can see.. does the same with shift switcher.. if i goto a blank desktop, i have flickering on the edges of what-ever is on the desktop beside it, like overlapping etc..

Tired the normal compiz settings, unredirect etc... refresh rates etc.. zero difference..  any ideas.?

---

### Post by QDR06VV9 on 2016-07-04
I'm seeing things as you describe with other apps and dual monitors with the same Nvidia Driver with nvidia-364 I did not see as much.
Just my 2 cents worth.

---

### Post by Plasma_NZ on 2016-07-04
Irony is... i was previously using NVIDIA-Linux-x86_64-361.42 - after reboot this issue appeared... only after not being able to fix it did i install NVIDIA-Linux-x86_64-367.27
 where the problem still persists... removed compiz and all config files etc... same problem still.. so it was something between current kernel and previous where the problem started..

---

### Post by Plasma_NZ on 2016-07-04
effectively broken my desktop lol.. pushing 3 screens and 3 xsessions.. should never update.. lol

---

### Post by QDR06VV9 on 2016-07-04
Yikes!! I am sorry to hear that.
By the way I may have some good news to ease your pain
Release: 15.04
Codename: vivid is no longer supported see this: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Plasma_NZ on 2016-07-04
i have 15.10 - that has its own huge set of issues when using 3 xsessions across 3 screens...  far more than 15.04... this single-screen supports killing ubuntu.
login loop that cannot be fixed when pushing 3 xsessions, keyboard across 3 xsessions - xev input for second k/m doesnt work properly etc.. list goes on lol - biggest issue is dpi on 3rd xsession thats different resolution that cant be changed cause xandr is blind to them and with no keyboard focus to other xsession results in unconfigurable..

---

### Post by QDR06VV9 on 2016-07-04
My best OS I have run in quite a few Version's is 14.04...smooth as cheese cake, everything just works well.
But that said everyone's mileage may vary.
Yakkety is shaping up pretty nicely, but not relevant here.

---

### Post by Plasma_NZ on 2016-07-04
yeah, this is running flawlessly apart from this clipping issue... driving me mental lol.. if someones got a fix or patch or solution.. sing out..! lol

---

### Post by CantankRus on 2016-07-05
Did you use the Proprietary GPU Drivers ppa  which can update other applications other than
the nvidia driver.
I only update the driver from this ppa.

---

### Post by Plasma_NZ on 2016-07-05
I use the ones provided by nvidia because with my setups they work best..... its a issue with the expo/wall plugin with something else.... changes have only happened with last kernel/files updates.. its not my drivers..

---

### Post by Plasma_NZ on 2016-07-05
Just like to point out rickus... i made a new profile... everything runs smoothly.... untill i used tweak-tool to disable desktop icons/short-cuts - when i turned them off, instant pollution as the pic in original post showed... turned it back on... problem goes... dunno if this helps your case.. just something strange i thought..

---

### Post by QDR06VV9 on 2016-07-05
> **Plasma_NZ said:**
> Just like to point out rickus... i made a new profile... everything runs smoothly.... untill i used tweak-tool to disable desktop icons/short-cuts - when i turned them off, instant pollution as the pic in original post showed... turned it back on... problem goes... dunno if this helps your case.. just something strange i thought..

Hey thanks for sharing your trouble shooting findings that's a good tip for those seeing similar problems.
Kind Regards

---

### Post by CantankRus on 2016-07-05
> **Plasma_NZ said:**
> Just like to point out rickus... i made a new profile... everything runs smoothly.... untill i used tweak-tool to disable desktop icons/short-cuts - when i turned them off, instant pollution as the pic in original post showed... turned it back on... problem goes... dunno if this helps your case.. just something strange i thought..
Can you show the actual tweak tool settings you changed?

---

### Post by Plasma_NZ on 2016-07-05
> **CantankRus said:**
> Can you show the actual tweak tool settings you changed?

It was gnome-tweak-tool - desktop - icons on desktop - set to on  

If i set it to off, it cause huge clipping resulting in a kick back to login-screen

---

