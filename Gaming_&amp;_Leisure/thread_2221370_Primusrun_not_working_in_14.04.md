---
title: "Primusrun not working in 14.04"
date: 2014-05-01
forum: Gaming &amp; Leisure
---

### Post by Mike Loubet on 2014-05-01
I upgraded to 14.04 and now the primusrun command no longer works, but optirun does. Obviously, I would like to continue using primus since it gives better performance, so is there any way I can get it working or do something else which gives comparable performance? Running primus with glxgears or steam gives me segmentation faults.

Running Kubuntu 14.04 64-bit

---

### Post by Jon Hanna on 2014-05-02
Due to the nature of primus, it might be worth giving some details of your system, particularly your graphics card. I can certainly attest that primus can run on 14.04, so it's not a case that it's an entire no-go.

Are you on 64 or 32bit and if 64bit you also have the 32bit primus libs?

Also, incidentally if you set your bridge in the config for optirun to be primus, the primusrun effectively **is** optirun.

I'd probably start from scratch with all of bumblebee, rather than trying to fix a bumblebee setup that got broken during an upgrade.

---

### Post by Mike Loubet on 2014-05-02
I have a GT640m with 6gb RAM and an i5 (can't remember the clockspeed or anything but I think it's ivybridge).

What I did (and now regret) is install nvidia-primus since I discovered that this now lets you switch between the nvidia and intel cards through nvidia-settings by installing that package and purging bumblebee. This worked, ran glxspheres64 and got decent framerates, however when I switched back to the intel card, I could no longer open nvidia-settings and switch to the nvidia card (I get a segmentation fault if I run it in the terminal). I have no idea what libs I have or how to check that.

Do you know how to set optirun to be primus? That sounds like the perfect solution for me, things were just fine as they were before and I like the control of running primus through the terminal (since all I use the nvidia card for is Steam and nothing else). I'm glad that Nvidia is starting to give native support for optimus in Linux, but the nvidia-primus solution is worse than the workaround at the moment, given that you need to log in and out again for it to take effect and I can't even select the nvidia card anymore.

EDIT: I can now switch between cards. This is a bug in nvidia-primus: [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1214508](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/1214508) - but I would still rather use the old primusrun solution.

---

### Post by Jon Hanna on 2014-05-02
> **Mike Loubet said:**
> What I did (and now regret) is install nvidia-primus...
...but the nvidia-primus solution is worse than the workaround at the moment, given that you need to log in and out again for it to take effect and I can't even select the nvidia card anymore.
I think you mean nvidia-prime rather than nvidia-primus, it's a different thing to primus.

**Nvidia-prime** is a new non-bumblebee way of using optimus. Maybe in the future it'll be better, and but right now it has issues in usefulness as you note. (That and adding "prime" to the list of words associate with a technology in which we also have "optimus" and "bumblebee" increase the number of Transformers-related results one gets back when trying to google about it).

**Primus** is one of two "bridges" used by bumblebee when it is using the Nvidia card (or the AMD card) to push data from that card through the other card to get to the screen. VirtualGL was designed for use in situations where a 3D renderer on a server machine is used by a client machine that need not have as powerful a graphics card. In a way therefore, bumblebee works with it by treating your machine as a server with a powerful Nvidia card, and a client without, and using VirtualGL to bridge between the two. Primus does more or less the same thing as VirtualGL, but it's only designed to work in the sort of one-machine situations you have, and so can be more efficient in that more restricted case. (It also assumes a few things aren't done by applications that VirtualGL will tolerate, meaning there could potentially be some applications only VirtualGL worked with).

> **Mike Loubet said:**
> Do you know how to set optirun to be primus?

Yes, but I'll have to come back to that, because right now you aren't using optirun at all. You'll need to uninstall nvidia-prime and re-install bumblebee. I got it working with 14.04 with both the nouveau and nvidia-331 drivers, though the latter needs a bit of a change to /etc/bumblebee/bumblebee.conf

 > **Mike Loubet said:**
> Do you know how to set optirun to be primus?

Okay, after you've replaced prime with bumblebee, and assuming you included primus in that installation, then primusrun will work again. As well as that optirun will use primus instead of VirtualGL if either it is run with the flag ```
-b primus
``` or if /etc/bumblebee/bumblebee.conf contains ```
bridge=primus
``` (the -b flag overrides this, the default "auto" uses virtualgl if available, primus otherwise though perhaps that will be reversed in the future).

It's worth setting ```
bridge=primus
``` in bumblebee.conf file, because this is what will be used if you have bumblebee.d running and you start an application through the bumblebee-ui indicator, or have that application set through bumblebee-ui to default to use with optimus.

---

### Post by Mike Loubet on 2014-05-05
Hi there,

Sorry for the primus/prime confusion. I'm aware of the difference, it was just a typo. I never considered the transformers references though haha, is that what they're named after?

I re-installed bumblebee and primus, and now I'm back to where I started, but worse because optirun doesn't work either. I'll walk you through what I did:

--purge removed nvidia-prime

Installed bumblebee, primus and nvidia-331 (got better performance with it on 13.10)

Followed the steps [here]("http://www.muktware.com/2013/12/install-nvidia-331-bumblebee-optimus-cards/18271") to get bumblebee working with nvidia-331.

Edited /etc/bumblebee/bumblebee.conf to replace bridge=auto with bridge=primus.

And now I get a segmentation fault (again) when running primusrun glxspheres64 and optirun glxspheres64 fails to open anything.

EDIT:

I purged everything and did the bumblebee installation with the 304 drivers and now optirun works, but again no primus (same segmentation fault)

EDIT 2:

Although optirun works with glxspheres, running games doesn't really work.

---

### Post by Jon Hanna on 2014-05-12
Could you show your whole bumblebee.conf, maybe cutting out the comments for brevity?

---

### Post by Peter_Solver on 2014-05-17
If you're using Bumblebee, does [COLOR=#333333][FONT=Helvetica]PRIMUS_UPLOAD=2 primusrun steam works on your end? Perhaps this has something to do with the bug in nvidia-primus. [/FONT][/COLOR]

---

