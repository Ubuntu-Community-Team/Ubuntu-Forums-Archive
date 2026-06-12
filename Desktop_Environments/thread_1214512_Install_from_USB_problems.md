---
title: "Install from USB problems"
date: 2009-07-16
forum: Desktop Environments
---

### Post by thundaraptor on 2009-07-16
Hello All,

Have just built a new machine.  ASUS M3A78-CM mb w/ Phenom 2.8 chip.  Have the machine put together but having trouble getting it to boot from a USB key.  I followed the instructions correctly from unetbootin to make the usb drive.  Am trying to install ubuntu 9.04 64bit.  I have set the usb drive as priority but do not seem to be able to get the system to activate the key.  I am exhausting what I know about this.  

The only noteworthy detail I can find is related to the boot priority.  If I enter insert the usb key with power off, power up the system and enter the bios the usb drive shows as a potential boot source.  Then I select it as priority, save exit and the system reboots.  Then on this go around with the usb key inserted, I get the motherboard splash screen (which is usually the prompt to enter the bios) but the system pretty much freezes displaying this splash screen.  

Conversely, if I have the system powered down, no usb key inserted and power up then enter the bios, the system has no option for usb as a boot preference.  then if I let the system continue to boot, the splash screen goes away and the computer displays a message to the effect of "please insert boot media into boot drive" so on and so forth.

Not sure what to do here but I need to figure something out as this machine is going to be great when finished.  Have another ati crossfire card compatible with onboard card and two 23" HD monitors.  Should be a nice ubuntu setup but can't make it work.  

I have posted this in a few other forms across the ubuntu help forum but not getting enough responses.  Would have thought this was a decent forum question.

Thanks for any help,

TR

---

### Post by jkbc on 2009-07-16
I had the same sort of problem with my netbook install recently. It turned out that I had performed the action to make the USB key bootable wrong. You may want to take another look at that.

---

### Post by thundaraptor on 2009-07-16
I changed the splash screen setting from display "enabled" to display "disable" and realized that there are more options like F8 to enter "select to boot from" screen.  So I have selected the usb key and unetbootin ran but it doesn't seem to be working.  It shows a screen that has "default" written on top then in yellow on the bottom written "press [Tab] to edit options and under that in white, "Automatic boot in xx seconds" which is a countdown but at the end of the countdown, it just resets itself back to 10.  If I push tab to select options "/ubnkern initrd=/ubninit _" is displayed in yellow.  I am not sure what to do about this.

---

### Post by thundaraptor on 2009-07-16
> **jkbc said:**
> I had the same sort of problem with my netbook install recently. It turned out that I had performed the action to make the USB key bootable wrong. You may want to take another look at that.

I thought I followed the instructions pretty carefully.  I even downloaded the iso and did the key again, manually from unetbootin to make sure that the file structure on the key pretty much looked the same.  

The only concern I have with unetbootin is that possibly, the app isn't running correctly inside ubuntu as when I run the exe file, i get the error message "7z not found.  This is required for either install mode.  Install the "p7zip-full" package or your distribution's equivalent."

Ideas?

---

