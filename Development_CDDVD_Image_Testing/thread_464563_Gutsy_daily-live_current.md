---
title: "Gutsy daily-live current"
date: 2007-06-04
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-06-04
I noticed .iso images showing up in daily-live current about June 3 or so.  Are these intended for testing yet?  Or is the date still June 7?  I haven't had much luck yet, with the June 4 .iso's about a second after Splash progress bar starts it drops into text mode with a Busy Box "can't access tty" (initramfs) screen.  Yes I entered a bug on Launchpad just in case it's useful for anyone #118717.
Cheers, Jerry

---

### Post by mrsno on 2007-06-05
> **jerrylamos said:**
> I noticed .iso images showing up in daily-live current about June 3 or so.  Are these intended for testing yet?  Or is the date still June 7?  I haven't had much luck yet, with the June 4 .iso's about a second after Splash progress bar starts it drops into text mode with a Busy Box "can't access tty" (initramfs) screen.  Yes I entered a bug on Launchpad just in case it's useful for anyone #118717.
Cheers, Jerry

Hi jerrylamos.
yes the images at [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) are the daily isos for testing, these could and most likely will be very buggy as it is the pre-alpha stage but we appreciate early testing.
Edit: all the testing will be done via [https://isotesting.stgraber.org/](https://isotesting.stgraber.org/) as with feisty fawn.

thanks for the testing, keep it up :)

---

### Post by jerrylamos on 2007-06-12
I've started entering/updating launchpad bugs for Gutsy, example 106864 "can't access tty" where Gutsy won't boot on a computer that Edgy boots fine on.  The bug fixes for 7.04 don't work for 7,10, at least not here.  Looking at the forums many people have hit this one on Feisty.

Another one is "persistent" mode which did a little bit today on 20070612; on one boot it did seem to recognize casper-rw and did load system files, however I couldn't get it to do that again and it didn't save a home text file.  That's bug 84591.  Some of us would really  like to see this one fixed short of going back to Edgy.

There are some anklebiters like shutdown & reboot CD eject immediately closes and can't get the CD out, shutdown doesn't shut down, reboot doesn't reboot, Another is the proverbial "network manager" which on Feisty disables my network card on boot, so I have to manually click the NM applet and click wired connection which then works.  Gutsy is no better.  And yes there are launchpad bugs entered/updated for these.

Good luck on tests & fixes.  Jerry

---

