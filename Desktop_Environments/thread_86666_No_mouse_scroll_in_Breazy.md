---
title: "No mouse scroll in Breazy"
date: 2005-11-06
forum: Desktop Environments
---

### Post by bradb on 2005-11-06
Hi all, just upgraded to Breazy from Hoary.  I was very pleased with Hoary, but I'm having a minor niggle with Breazy.  I can't seem to get my mouse scroll going.  I have a Toshiba Satellite 2410, the touchpad has two buttons and a scroll wheel that can be pressed to act as a third button.  The middle click functionality of the wheel works.  The scroll wheel on my USB mouse also doesn't work, but does work on my desktop Breazy install.
From my xorg.conf file
> 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        #Option         "Protocol"              "ImPS/2"
        Option          "Protocol"              "PS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

The default protocol of ImPS/2 makes my mouse crazy, scroll wont work, buttons are unreliable & dragging a scrollbar causes the scrollbar to move up and down eratically - though I am sure that I used to use ImPS/2.

The rest of my xorg file is based from here [http://www.thorstenhaas.de/toshiba2410/](http://www.thorstenhaas.de/toshiba2410/) - this file also uses ImPS/2.

Edit - xev isn't getting scoll events from the wheel or from the USB mouse.

Any hints & tips?  Does this sound like a kernel or Xorg thing?  I am running
brad@toshy:~$ uname -a
Linux toshy 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
Xorg is standard Breazy & looks to be 4.4rc2.

Thanks
Brad

---

### Post by cpbl on 2005-12-02
I also have a Toshiba Satellite 2410!  I am trying Breezy from a long history with Mandriva -- never any trouble with the touchpad. With Ubuntu Breezy/ 5.10 the mouse is active, the buttons seem to exist, but when I drag a scrollbar down or switch pages, etc, something is fighting to pull the cursor back to where it was. As a result, for instance, I cannot scroll down in any application. Also, the scrollwheel does not work at all.
 I can find no hardware configuration tool, mouse tester, etc in Ubuntu.

I have tried using the same xorg.conf lines as I used successfully under Mandriva, etc -- no help.

I will try changing to "PS/2" protocol (thanks!), but it sounds like this has only helped you part way.

Brad, I'll obviously be interested to find a solution too. Thank you!
Chris in Vancouver, BC.

---

