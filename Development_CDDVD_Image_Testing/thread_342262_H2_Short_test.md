---
title: "H2 Short test"
date: 2007-01-19
forum: Development CD/DVD Image Testing
---

### Post by Jose Catre-Vandis on 2007-01-19
Test case type: Ubuntu Herd 2, Alt Install CD, manual partitioning
Image ID: 20070110.3
Date of testing: 20 Jan 2007
md5sum confirmed: Yes
Pass/Fail:
Bugs identified:
Other comments:
Pass/Fail
Bugs identified

Installation planned to a spare partition (hda10) on a multiboot hard drive with three other OS onbaord and a couple of data parititons.

Boot OK
Text mode install
After keyboard selection long wait (a few minutes) before host name screen
Then long wait again after entering host name before hardware detection gets going
No option for manual partitioning so round and round in circles trying the "Guided" options for about 20 minutes trying the other options. Finally get options to set root folder on hda10, and base system install commences.

This was a pig!

Chose not to install grub, and rebooted into my dapper, to discover vmlinuz and intrid names and paths, then edited menu.lst.
reboot and selected Fiesty in grub, and booted up OK

Things that didn't work:

3. Sound on login screen (drums) worked but  No sound on login and No sound server present
lsmod indicated all sound services loaded?
4. Unable to "confirm successful startup" and no "Working with desktop" present
9. USB Flash drive launched RythmBox, not Nautilus (no sound files present on flash drive)
10. Nothing in System>Adminstration that needs sudo works, either refuses to even load, or tells me I do not have rights
I could sudo OK in terminal

Everything else on short test 1-10 worked

As expected (because I have an ATi 9500 card) very slow 2D motion and poor background on the vesa setting

Not my usual ubuntu experience at all :)

---

### Post by pochu on 2007-01-20
Can you search for that bugs on Launchpad and, if they haven't been reported, do it?

Thanks
Pochu

---

### Post by Jose Catre-Vandis on 2007-01-20
I could only find three fiesty bugs on Launchpad - I am sure there are more???

---

### Post by pochu on 2007-01-20
Yes, there are more. Use the [search funcion]("https://bugs.launchpad.net/ubuntu/+bugs?advanced=1").

---

