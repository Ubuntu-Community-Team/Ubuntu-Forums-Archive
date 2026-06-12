---
title: "Projector not working after upgrade to 11.10"
date: 2011-11-01
forum: Desktop Environments
---

### Post by lucacerone on 2011-11-01
Dear all,
I've an nVidia graphic card on my laptop and restricted driver installed.
Before when I connected my laptop to a projector (or to an external tv/monitor) I was able to clone my screen by pressing FN+F4.
After the upgrade to Ocelot I'm no longer able to clone my screen,
nor pressing FN+F4 nor opening the nVidia settings software,
nor trying to detect displays using the systems settings.

This is quite annoying, I use my Ubuntu laptop to present some course material and some of my research work, and it has been a bit embarrassing
having to borrow a laptop from the audience in order to show my work.

How can I fix things back? (I have no idea where to start...)
Any help is really appreciated, thanks a lot for your help in advance.

---

### Post by typhoon_tip on 2011-11-01
I am trying tomorrow with my 11.10 and a projector that was notoriously a trouble maker for some reason, on my T400 with ATI Radeon HD video card.

If I have the same problem, then is definitely something related to Ubuntu. Otherwise might just be other things, let's see.

Any other have this problem with NVIDIA ?

---

### Post by lucacerone on 2011-11-02
Unfortunately I don't have any colleague or friends using
Linux (and having a nVidia card) I can ask to..
Let me know if it works for you or not...
My first thought is that the xorg file has been messed up, but I don't know how to  check this...
Thanks for the advice!

---

### Post by infinitybot on 2011-11-02
Can You please tell me your graphic card model?
```
lspci | grep VGA 
```
```
 sudo lshw -C video 
```

---

### Post by lucacerone on 2011-11-02
Thanks a lot infinitybot!

The output to lspci | grep VGA is:
```
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)

```
and to sudo lshw -C video is:
```
*-display               
       description: VGA compatible controller
       product: C67 [GeForce 7150M / nForce 630M]
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:d0000000-dfffffff memory:f4000000-f4ffffff memory:80000000-8001ffff
```

---

### Post by typhoon_tip on 2011-11-03
Ciao Luca,

Is definitely something related to the NVIDIA driver you have installed, because it worked like a charm on my Ubuntu 11.10 with fglrx driver from repositories.

It was not working with Ubuntu 10.04 and 10.10, particularly with this type of projector.

Are you using repository NVIDIA drivers or have you installed the one from NVIDIA website ? If so, could be worth to clean everything up and install the rep one.

---

### Post by lucacerone on 2011-11-03
Thanks a lot Typhoon!
I'm not sure what driver I have installed...
I used the ones in the "restricted hardware" section of Systems Settings.
Are those the fglrx driver you mentioned in your post?
Yesterday though I noticed that I didn't have the recommended version
installed.. so I deactivated the installed version and installed the recommended one.. I'm sorry I don't have a projector at the moment to test whether it works or not now...

Thanks for your help in any case, at least I have hope to make it work one day :)

---

### Post by typhoon_tip on 2011-11-03
You will most likely be able to make it work smoothly ! ;)

You do not use fglrx because that is the driver for ATI, NVIDIA has its own, but same philosophy. Indeed, you were not using the current version if you had not chosen "recommended" as you option. Try it out as soon as you have a chance and let us know.

---

### Post by jdggra on 2011-11-10
Did precisely that and it worked.  The only problem is when I launch nvidia-xserver-settings after I've set the twin view.  It freezes the screen.  The solution I found was changing to tty screen (ctrl+shift+f8) and then returning to x-screen (ctrl+shift+f7).  Then everything comes back to life!

Hopefully they'll fix this...

---

### Post by typhoon_tip on 2011-11-10
> **jdggra said:**
> Did precisely that and it worked.  The only problem is when I launch nvidia-xserver-settings after I've set the twin view.  It freezes the screen.  The solution I found was changing to tty screen (ctrl+shift+f8) and then returning to x-screen (ctrl+shift+f7).  Then everything comes back to life!

Hopefully they'll fix this...

Yeah, some workaround sometimes still necessary with displays. I also get some resolution adjustment errors on some occasions, but basically is working.

And don't think that MS is managing this well. Totally we have over a thousands computers under management, including a lot of laptops. The case of a Lenovo X200i laptop with Win 7 was incredible. As soon as you connect the damn projector (same that was causing trouble to me) entire thing entered an halt state, not even a blue screen appeared, and it was necessary to shutdown the laptop with power button. At least with Linux you have the chance to fix the problem, in that case the guy remained with the problem until he quit :P

---

### Post by baibhav on 2012-02-28
This solved my problem, in case anybody is still looking for the solution.

[http://www.baibhav.com.np/article/6-...0-solved-.html](http://www.baibhav.com.np/article/6-...0-solved-.html)

---

