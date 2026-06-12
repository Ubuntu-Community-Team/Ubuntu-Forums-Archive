---
title: "Standby does not work in Ubuntu Intrepid, but instead shuts down the computer"
date: 2009-02-15
forum: General Help
---

### Post by rdibley on 2009-02-15
Standby doesn't seem to be working correctly for my computer.  When I select standby, the screen fades as it does when locking the screen, and then transitions to a blank text-mode screen with a blinking cursor at the upper left corner.  The computer then shuts down the hard drives, the fans, and the rest of the system as you would expect for a system going into standby.  Also, the numlock, capslock, and maybe the scroll lock lights flash once and then go out, just as the machine is shutting down.

Once it's in this state, no pressing of the keyboard (both a USB and a PS2 are hooked up), nor moving the mouse will bring the machine back from this state.  Only pressing the power button does anything, and then it boots up, going into the regular POST and boot routine as if the machine was powered off.  In no way does it do anything that would be considered "resuming" from standby; just a normal boot.

I am running Ubuntu Intrepid 8.10 on an Abit KV8 Pro motherboard, and AMD 64 3400, and an Nvidia 6800 GTS video card.  I am running the Nvidia accelerated graphics driver 177, along with the Compiz fusion accelerated desktop.  I have enabled suspend to ram (S3) in the bios.  There are two other options, one for the video BIOS and one for allowing USB to wake the computer.  I have tried changing both of these, but they don't fix the problem.  I have also tried using the standard (non-Nvidia) driver, but that didn't do anything either.

This same computer, with the same hardware, was transitioned over from a Windows XP machine, and suspend worked perfectly on that, so I know that the machine is capable.  This is my first experience with Ubuntu (have used Slackware, Redhat, Debian over the past 10 years), and I am impressed with how far Linux has come.  But until simple things like this can be made to work "out of the box", Linux will remain a hobbyists OS. :(

---

