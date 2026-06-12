---
title: "Joe"
date: 2010-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jbissett on 2010-10-06
I had 7.04 installed on an old Dell Dimension XPS T450 computer.  It ran fine.  I just upgraded thru mini-ios to 10.04.1.  The install went without problems, but after GRUB installed and it told me to remove the CD and reboot, the reboot happened but no monitor display took place.  I rebooted several time more with no success.  The blue Dell logo displays, then a blinking cursor in the upper left corner of the monitor for a few seconds, then the monitor goes blank.  I know the Ubuntu is loading because of the HD activity light, etc.

---

### Post by mörgæs on 2010-10-07
This could be due to a screen card with poor support for Linux. Which screen card do you have?

By the way, a more descriptive title will probably give you more answers.

---

### Post by jbissett on 2010-10-07
Yes, it was my first forum message and I screwed up.  I posted it again with a much more descriptive title.  P4man has been helping me.

As to your question:  I don't have a clue.  It is an old Dell machine that I got from my son-in-law that I want to use to test and learn Ubuntu.  I am a total newbie at this time.

---

### Post by oldfred on 2010-10-07
I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

---

