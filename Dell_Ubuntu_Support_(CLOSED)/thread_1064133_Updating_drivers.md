---
title: "Updating drivers?"
date: 2009-02-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wolfyking2 on 2009-02-08
How would I do this?  Because my graphics on this computer suck and I really want my games to work.  A lot of them don't work.  I have an intel card (i'm pretty sure)

---

### Post by ugm6hr on 2009-02-08
Intel graphics aren't fantastic.

But they are well-supported in Linux.

You can check with - post output here for further advice:
```
lshw -class display
```

If it is Intel, it is unlikely that a newer driver will make a big difference.

What version of Ubuntu are you running?

---

### Post by wolfyking2 on 2009-02-08
Well, heres the output

user@ubuntu:~$ lshw -class display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810

And I'm running ubuntu 8.04

---

### Post by ugm6hr on 2009-02-08
I think you already have the latest driver.

In any case - here they are:
[xserver-xorg-video-intel]("apt:xserver-xorg-video-intel")
[xserver-xorg-video-i810]("apt:xserver-xorg-video-i810")

I think either of these will work (although former includes more chipsets).

---

### Post by wolfyking2 on 2009-02-08
Yea, they are...

sadface :(

---

### Post by beatgr on 2009-02-08
> Intel 82845G/GL
Yes, very familar with that chipset.  It was used in the the early Shuttle-X computers (I still use mine, built in 2002 as a daily driver).

I would not recommend the Intel chipset for games, 
go with Nvidia add-in card (unless this is a laptop).  
Intel walked away from this early attempt at graphics chip sets about 10 years ago(ATI was still a player then).  Intel made a strategic mistake, once you look at Nvidia Ion !

Nvidia is walking away with this marketplace (leading with gaming).  
See the Nvidia ION at CES last month?
Here is the photo and article:

Small chip on side is 1.6GHz Atom 330 CPU
Large chip is NVIDIA's GeForce 9400M Graphical Processing Unit (GPU)
[http://www.engadget.com/2009/01/12/nvidia-ion-platform-gets-demonstrated-at-ces/](http://www.engadget.com/2009/01/12/nvidia-ion-platform-gets-demonstrated-at-ces/)

beatgr

---

### Post by wolfyking2 on 2009-02-09
Yeeaa, I noticed a lot of people hav nVidia cards (or however you spell them) we go this computer from a university surplus store, so they weren't supposed to be for gaming or anything ;(

---

### Post by SunnyRabbiera on 2009-02-09
Yeh I dont think drivers will help you in this case, Intel cards work well for the most part even in linux but they lack the umph required for some games.
I myself have a intel915, works well but I know it has limitations

---

### Post by beatgr on 2009-02-09
> .. we got this computer from a university surplus store, so they were not used for gaming (more for business computing)
Well, if you expected this surplus acquistion to be "game ready" -- that was a poor assumption.
NVIDIA makes several video cards, and older models are available CHEAP either surplus, eBay or closeouts from normal computer hardware suppliers.  The GeForce line is quite good.
[http://www.nvidia.com/page/home.html](http://www.nvidia.com/page/home.html)

beatgr

---

