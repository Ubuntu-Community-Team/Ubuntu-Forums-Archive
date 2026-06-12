---
title: "Visual Effects freaking out, need help."
date: 2009-02-12
forum: General Help
---

### Post by jpcafazza on 2009-02-12
Hey all! Whenever I turn my visual effects on to "Normal" or "Extra", my open windows leave a black spot on my desktop and have a boarder around them. Anywhere that I drag the window turns my desktop black. Whenever I turn "None" on for visual effects, everything is fine. Can someone help me please?

---

### Post by lykwydchykyn on 2009-02-12
Sounds like your video card does not support desktop effects very well.  What is the make and model of your computer, and can you post the output of this command:
```

lspci

```

That will give us some starting information to try to troubleshoot.

---

### Post by jpcafazza on 2009-02-12
Thanks for the help. Here it is:

[[IMG]http://img19.imageshack.us/img19/4128/screenshotjohnpauljohnlhs2.th.png[/IMG]](http://img19.imageshack.us/my.php?image=screenshotjohnpauljohnlhs2.png)

I also did another test for Compiz-check to see if it was a problem with it:
[[IMG]http://img14.imageshack.us/img14/138/screenshotjohnpauljohnllx1.th.png[/IMG]](http://img14.imageshack.us/my.php?image=screenshotjohnpauljohnllx1.png)

I really don't understand what it could be because it was working just fine earlier yesterday with the "Extra" visual effects checked.

---

### Post by lykwydchykyn on 2009-02-12
Looks like you've got an Intel 945 graphics chip.

Intel stuff usually works ok, but I've run into situations where I had to upgrade the BIOS to make it work properly.  I've also heard there have been issues with the Intel drivers in Intrepid, though my two intel-chip machines (got one 855gm and one 965) have been working ok.

So that's what you're probably up against.  Are your packages and BIOS both up-to-date?

---

### Post by jpcafazza on 2009-02-12
To be honest, I'm not sure how do I check?

---

### Post by lykwydchykyn on 2009-02-12
Well, updating your system is just a matter of installing updates when you see them come available.  I believe in the default setup there's an applet to notify you of updates.

As for BIOS, you need to check with your PC vendor (Dell/compaq/gateway/etc), or if it's a custom-built then your motherboard manufacturer.  What's the make/model of the PC?

---

### Post by jpcafazza on 2009-02-12
I know Ubuntu is up to date. My laptop is a Dell Inspiron E1505, it's about 3 years old i believe.

---

### Post by lykwydchykyn on 2009-02-12
According to support.dell.com, the latest BIOS for that is A17.  When you boot the machine, it should have an "A number" somewhere at the bottom of the screen, under the dell logo.  If the number is less than 17, I'd recommend upgrading.

Dell has a repository and a utility that allows you to update your BIOS using synaptic.  I have it set up on my Optiplex at work, but I don't know if it supports all models.  It was kind of tricky to get set up, tbh.  So if you want to update your BIOS (and you probably do, based on my many Dell experiences), your options are:

 - Boot to Windows (if you have it) and run the BIOS update from windows
 - Download the BIOS update and put it on a CD with freedos, then install it from the boot CD
 - Have a look at this and see if your model is supported: [http://www.ubuntu-unleashed.com/2007/09/howto-easily-upgrade-dell-bios-in.html](http://www.ubuntu-unleashed.com/2007/09/howto-easily-upgrade-dell-bios-in.html)

---

### Post by jpcafazza on 2009-02-12
So my BIOS on startup says A14, obviously out of date huh?

---

### Post by lykwydchykyn on 2009-02-12
Yup

---

### Post by jpcafazza on 2009-02-13
Hey lykwydchykyn, I updated my BIOS to A17 and the problem is still persisting. Anymore thoughts?

---

