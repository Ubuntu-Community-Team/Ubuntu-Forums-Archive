---
title: "Ubuntu 7.10 on a Dell 1721"
date: 2007-10-31
forum: Dell  Ubuntu Support
---

### Post by okilinux on 2007-10-31
I just picked up a Dell 1721 from a friend that purchased the laptop for gaming and was not happy with the performance with Virista (Vista) so I was able to get it at a good discount.  The first thing I did was throw in the Ubuntu 7.10 Live CD to see what would happen.  What followed was hours of tinkering to get a dual boot system with Virista and Gusty.  On Ubuntu I have the video working at a full 1920x1200, the sound works, and the wireless works.

The first issue is booting from the Live CD.  The boot will fail and give you a blue screen that says the video server failed to start 6 times or something like that.  Do not hit OK.  Instead use Ctrl+Alt+F2 to switch to a CLI and kill the gdm process.  Then just type startx and Gnome should appear.  This will allow you to install the system.

Once the system has been installed and you reboot you will get the same blue screen again.  Only this time startx will not work.  Do the same Ctrl+Alt+F2 to get to the CLI and kill gdm.  Then run sudo dpkg-reconfigure xserver-xorg to reconfig the xserver.  I used the defaults and set the video card to vesa.  Then startx worked and gave me a low res 1600x1200 screen.  Next you need to set up your sources to allow proprietary software in System -> Administration -> Software Sources and install the restricted drivers by going to System -> Administration -> Restricted Drivers Manager.  Be sure to install the ATI and Firmware drivers.  You system will need to be reboot after the driver installation.  Once the computer has reboot you will still have a 1600x1200 screen.  Now go to System -> Administration -> Screens and Graphics.  The Monitor model will be Custom 1.  Change the model to LCD Panel 1920x1200 and check Widescreen monitor.  Reboot the computer and you will have a nice crisp 1920x1200 display.

Next for sound you need to do sudo apt-get install linux-backports-modules-generic and then reboot.  I do not know what this does but it made my sound work.

My wireless card works as well.  I do not know if any of the above things made it work but sometime during all of the above I noticed that my wireless card seemed to be working.  Just remember that the 1721 has a switch on the left-hand side that turns the wireless on and off.  If the switch is off your wireless will not work.

The multicard reader works and detects my new SD card that would not work on my other Dell laptop.  

There is a Bluetooth icon on the desktop but I do not know if it works as I have not other Bluetooth devices.

The front buttons work at least for volume control.  I have not tested any of the other buttons.

I have not had time to try anything else such as the webcam or the multicard reader but I intend to keep at it.

I have also not had time to play with the power options

Good luck to all.  I hope this helps.

---

