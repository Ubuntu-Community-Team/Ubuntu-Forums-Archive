---
title: "keboard suddenly upper case and alt-tab app list moves backwards"
date: 2007-10-16
forum: Desktop Environments
---

### Post by guitar_dude on 2007-10-16
Have an odd problem, randomly the system will go upper case without warning.  Holding down the shift key will not put the keys in lower case mode so of course I can't run any commands like dmesg or cat log files.  Also when alt-tabbing through the app list it moves backwards.  

At times the system will recover, i'll just lock the screen and make my social calls come back and it's fixed.  A timeout somewhere?  I tried cntrl-alt F-keys to get to console mode but it was still uppercase and of course I couldn't log in.  Ended up power cycling the box.

Specs:
---------------
stinkpad t60p 2GB of ram, dual core 2.4ghz.
running dual head with fglrx driver.
 uname -a
Linux xxxx 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

thanks in advance.

--------- small snip of xorg.conf ------------

Section "Device"
        Identifier  "ATI Video Card"
        boardname   "ATI Radeon (fglrx)"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
        screen 0
        vendorname  "ATI"

        #Specific for dual display!
        Option "MergedFB" "True"
        Option "EnablePageFlip" "True"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "True"
        Option "MergedXineramaCRT2IsScreen0" "True"
        Option "CRT2Position" "RightOf"
EndSection

Section "Device"
        Identifier  "ATI Video Card 2"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
        screen 1
        vendorname  "ATI"
EndSection

---

### Post by konungursvia on 2007-10-16
I had this. Maybe your shift key is physically stuck? I'd bang on them both, to make sure.

---

### Post by Beggar on 2007-10-16
You have a shift key stuck down. Try pressing them both repeatedly, if its a real keyboard, try popping the key off the top and cleaning it out as best you can.

---

### Post by mumushi on 2007-10-17
the most obvious problem we can see is what others had said. Try checking if it was stucked or if nothing happens try using a diffrent keyboard to make sure the keyboard really is the problem.

---

