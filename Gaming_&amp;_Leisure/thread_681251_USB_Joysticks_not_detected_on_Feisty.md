---
title: "USB Joysticks not detected on Feisty"
date: 2008-01-28
forum: Gaming &amp; Leisure
---

### Post by Andrew Pape on 2008-01-28
Hi,

I've been running Feisty for ages, throughout 2007,  and my USB joysticks have always worked out-of-the-box.  But after a hardware bomb I've had to reinstall everything, including Feisty, and neither of my USB joysticks work. I saw a post about jscalibrator (2006), where the posters said there was a bug in ubuntu with regard to calibration. But I've never had to run a calibrator before, and I've been using the joysticks all of 2007. I've tried changing the BIOS, thinking that might make a difference, but no go. I've tried the calibrator, and it doesn't detect any movement or buttons.

Help greatly appreciated.

Cheers,

Andrew.

---

### Post by hikaricore on 2008-01-29
Does **dmesg** show any output when you plug the device in?

---

### Post by acoustibop on 2008-01-29
I would get rid of jscalibrator unless you're using Kubuntu, Andrew.  I don't think it's the cause of this problem since it's not reporting any thing, but it has a nasty habit of disabling controllers while reporting them as working.

People think the controller must be fine, since jscalibrator reports it as working, and can't understand why it won't work in games.  Try joystick if you need a calibrator - it's command line, but easy to use.

---

### Post by frenchn00b on 2008-01-29
> **Andrew Pape said:**
> Hi,

I've been running Feisty for ages, throughout 2007,  and my USB joysticks have always worked out-of-the-box.  But after a hardware bomb I've had to reinstall everything, including Feisty, and neither of my USB joysticks work. I saw a post about jscalibrator (2006), where the posters said there was a bug in ubuntu with regard to calibration. But I've never had to run a calibrator before, and I've been using the joysticks all of 2007. I've tried changing the BIOS, thinking that might make a difference, but no go. I've tried the calibrator, and it doesn't detect any movement or buttons.

Help greatly appreciated.

Cheers,

Andrew.

Is it another bug or it works great with Debian Stable, if by chance you have a server with it?
if nto working for feisty, hence $ reportbug

---

### Post by Andrew Pape on 2008-01-29
Hi guys,

thanks for all the promt mails. Having a new, fast internet connection, I downloaded all the updates to Feisty. And that solved the joystick problem! I hardly ever used to get updates with Feisty, but the joystick fix was presumably one of the updates that I got last year before I had to reinstall recently.

So, to anyone with joystick problems and Feisty, make sure to get the updates.

Thanks again everyone.

Cheers,

Andrew.

---

### Post by frenchn00b on 2008-01-30
> **Andrew Pape said:**
> Hi guys,

thanks for all the promt mails. Having a new, fast internet connection, I downloaded all the updates to Feisty. And that solved the joystick problem! I hardly ever used to get updates with Feisty, but the joystick fix was presumably one of the updates that I got last year before I had to reinstall recently.

So, to anyone with joystick problems and Feisty, make sure to get the updates.

Thanks again everyone.

Cheers,

Andrew.
 
Sounds weird a bit for a distro. I am hope that feisty new incoming users to Ubuntu world will know the trick.

---

