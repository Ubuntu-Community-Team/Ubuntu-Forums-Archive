---
title: "Grub Grub Grub.  Keyboard not responding in Grub."
date: 2009-02-26
forum: General Help
---

### Post by redonwhite on 2009-02-26
Hello,

I recently just installed a new motherboard.  Gigabyte MA790X-UD4.  After some tinkering around in my system I shut the case and powered my baby on.  New POST and BIOS woo hooo!  Then grub started up and this is where i can usually select to either boot my Ubuntu 8.10 Drive or my Windows XP Drive.  But my keyboard will not respond to any input.  The keyboard lights up. (back-lit keys).  And the keyboard also respond when I enter the BIOS.  But doesn't seem to respond when Grub loads up.  Any ideas on what might be causing this or what i can do to fix this?  Thanks for your time!

---

### Post by kmac on 2009-02-26
Have you tried with another keyboard?

If possible (and this will be old-school) give it a shot with a PS2 keyboard. This will narrow down a few hardware possibilities.

---

### Post by redonwhite on 2009-02-26
> **kmac said:**
> Have you tried with another keyboard?

If possible (and this will be old-school) give it a shot with a PS2 keyboard. This will narrow down a few hardware possibilities.

shoot, Dont have a ps2 board on me right now.  I can borrow one tomorrow.  Tried a different USB keyboard.  Same issue.  Its odd because besides that OS selection screen the keyboard works perfectly for everything else, BIOS, and Ubuntu.

---

### Post by dcstar on 2009-02-27
> **redonwhite said:**
> shoot, Dont have a ps2 board on me right now.  I can borrow one tomorrow.  Tried a different USB keyboard.  Same issue.  Its odd because besides that OS selection screen the keyboard works perfectly for everything else, BIOS, and Ubuntu.

Check any keyboard setting in the BIOS - you many find an "Emulation" setting you can enable.

---

### Post by redonwhite on 2009-02-27
Thanks for the help all.  I ended up going into the BIOS and found an option to Enable USB Keyboard during MS-DOS.  Enabled that and now it works!

---

