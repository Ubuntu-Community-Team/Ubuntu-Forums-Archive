---
title: "ATI and OpenGL?"
date: 2006-01-17
forum: Desktop Environments
---

### Post by crispy_420 on 2006-01-17
Is there a good test to see how well my graphics card is performing?

My card is a ATI Radeon 9800 Pro (128MB) and I installed the drivers from the ATI website. I just want to know if I'm getting all I can from it since some screen savers seem very slow, as opposed to sample view in setup.

I see a lot of talk as to setup but how bout testing. Or could I get a link to the proper setup of the these drivers? Maybe I did something wrong and OpenGL is not enabled.

Any help out there or anyone else running a similar card that can point me in the proper direction. I just see so many posts and don't want to mess around, I just want to get it done right the first time with out trashing my system and having to reconfigure.

THANKS!

**_My Hardware:_**

Intel board D845BG
Intel P4 2.0GHz 400MHz FSB
1024MB DDR
ATI 9800 Pro 128 MB
(think that is all that matters for this?)

When I test a screen saver it is very choppy, something must not be setup correctly.

---

### Post by Neo- on 2006-01-17
You can test in like glxgears
(Terminal and command: glxgears)
if you dont get more than 1000fps then there is something wrong..

---

### Post by chele on 2006-01-17
3D graphics? What for? My monitor is two dimensional.

---

### Post by JAwuku on 2006-01-17
Hi there,

You can test whether the dedicated ATI driver is installed by running the command in the terminal:

```
fglrxinfo
```

If you either get an error or you get something that says "Mesa", the ATI drivers have not been installed completely.

Mesa, by the way, is the software emulation for 3D graphics, and as it is mimicing the hardware, it is much slower than if you were running 3D applications on the ATI card directly.

To remedy this, verify in Synaptic that the package **xorg-driver-fglrx** is installed already. If not, then install it.

You then have to do further simple setup steps as detailed in the Ubuntu Wiki:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

Once you've done the steps and rebooted, then type **fglrxinfo** and the ATI model should show up. Try the screensavers, and they should be much quicker.

---

### Post by JAwuku on 2006-01-17
[QUOTE=chele]3D graphics? What for? My monitor is two dimensional.[/QUOTE]

Yes, our monitors are all 2D :), but many complex graphical applications are coded to use 3D graphics, using things like vectors.

All modern graphic cards sich as Nvidia Geforce and ATI Radeon have dedicated processors to handle 3D graphics quickly, to free up processing power in the main CPU to to other things. This speeds up the process of showing graphics.

It's analogous to our own eyesight, where a 2D image is formed in the retina at the back of the eye, and this is transformed into a 3D image by the interpretation of the brain.

Sorry if the above explanation may not be very clear, maybe someone else can shed light on this? :rolleyes:

---

### Post by crispy_420 on 2006-01-17
OK followed those instructions and it appears to be working. THANKS!

But how do I test how well it is doing? When you type glxgears in konsole, it doesn't give you fps. But I did see a dramatic improvement.

But my problem was solved and that is all I wanted, any thing more is like icing on the cake.

---

### Post by N6546R on 2006-01-17
glxgears -printfps

The new switch is a 'feature'.

For anyone having trouble with the driver, make sure that you have the appropriate restricted-packages for your kernel installed. It's mentioned in passing in the document cited above, but it's easy to miss. The actual driver is in the restricted package. **lsmod | grep fglrx** should return a value, if it doesn't, the driver module is not loaded.

P


[QUOTE=crispy_420]OK followed those instructions and it appears to be working. THANKS!

But how do I test how well it is doing? When you type glxgears in konsole, it doesn't give you fps. But I did see a dramatic improvement.

But my problem was solved and that is all I wanted, any thing more is like icing on the cake.[/QUOTE]

---

### Post by crispy_420 on 2006-01-17
Seems to be working now. 

glxgears -printfps = over 4500 fps

From what I have read that is pretty good.

Again thanks guys.

---

