---
title: "Setting default font for text-based terminals"
date: 2009-03-25
forum: General Help
---

### Post by RailRover on 2009-03-25
Hello,

On my Ubuntu 8.04 install, I have turned off the splash screen to show any errors or warnings during boot-up.  About halfway through the boot process, the text font changes from my very readable normal text font to a "skinny" looking text font, that's not quite as readable to me.  I have tried changing the default text font by passing in the "vga=" kernel parameter in the boot entry in **menu.lst**, and on boot-up the font will initially change, then it resets back to the "skinny" font.  This font also winds up being used in the text-based virtual terminals too (Ctrl-Alt-F1 through F6), and is just ugly to me.

Does anyone know if it's possible to set the system to not change the text font during boot-up?  Believe it or not, I actually use the text terminals occasionally (hey, I'm an old guy).  It STARTS booting with the font I'd like to use, and I'm wondering what changes it.

Thanks in advance!

RR

---

### Post by RailRover on 2009-03-26
After some googling tonight, I found how to do this, so I'll post it here for posterity.  :)

To set the font for the text console, you use the utility "console-setup".  Enter this command:

[FONT="Courier New"]**sudo dpkg-reconfigure console-setup**[/FONT]

This will launch the utility and start asking you questions.  Go through the keyboard questions, then you will come to the display questions and be asked what font to use, "Fixed" or "VGA".  Mine was defaulting to "Fixed", so I chose "VGA", and then chose a size of "16" on the next screen.  When finished, reboot, and your font changes will be in effect.  Now I have my old font back!

RR

---

