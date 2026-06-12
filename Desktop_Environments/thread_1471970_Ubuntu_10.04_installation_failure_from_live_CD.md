---
title: "Ubuntu 10.04 installation failure from live CD"
date: 2010-05-04
forum: Desktop Environments
---

### Post by Garry_L on 2010-05-04
I currently have the Ubuntu i386 9.10 desktop working on my PC.  I intend to upgrade to 10.04, but before that I want to get a new installation CD for a friend just changing to Ubuntu, & for my emergency use.

I had previously (Nov 2009) gone through the CD creation process for 9.10.

I have just downloaded Ubuntu i386 desktop 10.04, & created a live CD.

I confirmed the MD5sums on the download before creating the CD.

I followed the steps in "Burning Iso Howto" from the Ubuntu Community Documentation.

Once the PC was in or past the boot stage, the display showed a dark pink screen, with the word Ubuntu plus the shape; under that were 5 dots, stepping through & changing from white to red, then red to white.

After some time, the arrowhead mouse symbol appeared (but it didn't respond to movements of the mouse).

Shortly after that a message was displayed:

"Installation failed.
The installer encountered an unrecoverable problem.
A desktop session will now be run so that you may investigate the problem, or try installing again."

There was an "OK" button, but the mouse would not respond, and the enter key has no effect.

In fact, no keys had any effect, & there was no light on the keyboard (usually the number lock light is on, but also when I pressed number lock or caps lock, their lights did not light up).

The only way that I could stop the PC was by pressing the power button.

I tried booting the PC with the live CD several times, but the same result occurred consistently.

Has anyone else had this problem?

Is it simply a problem with the created CD?  Would creating  a fresh CD resolve the problem?

Regards, Garry.

---

### Post by QIII on 2010-05-04
The iso md5sum may have given you the correct hash, but that is only one  part of the process.  The other is burning the iso to disk, of course.

Errors may be introduced there as well.

Try selecting "Check disk for errors" and see what happens.  If it turns  out the disk is bad, try re-burning the iso at the slowest possible  speed your burning software will allow (even if that is painfully  slow!).

Again, check the disk for errors.

Sometimes it takes making a few coffee cup coasters.

---

### Post by Garry_L on 2010-05-04
Hi QIII,

Thanks for your response.

Can you tell me from where I can do the CD check that you suggested?

Regards, Garry.

---

### Post by QIII on 2010-05-05
Are you even getting to the point where you have the selection to "Try"  "Install" or "Check"?

If not, eliminate hardware issues by checking to see that another CD can be read by the device.

---

