---
title: "how do I install remote networking via a network connection"
date: 2006-07-30
forum: Desktop Environments
---

### Post by brickbat on 2006-07-30
Hi,

I have an Ubuntu box with no monitor, keyboard, or mouse.  I have already setup the bios to boot without a keyboard

How can I do the following?

1. Login via network from Windows
2. Install a remote desktop via cli
3. setup and run said remote desktop server
4. Set up Ubuntu to run the remote desktop server on boot
5. Connect to the remote desktop in Linux
6. Connect to the remote desktop in Windows

---

### Post by brickbat on 2006-07-31
bump

---

### Post by RAOF on 2006-07-31
If you've had the foresight to install an ssh-server on the Ubuntu box, then, yes.  Get an ssh client for windows (google for putty ssh), login to your Ubuntu box.

Then, you can do anything you could from the command line, so I'd suggest finding some remote desktop howtos, such as: [this one](http://www.ubuntuforums.org/showthread.php?t=97277&page=7&highlight=freenx+howto+dapper).  You should change all references to "breezy" to "dapper".  So it would be **dapper-seveas**, etc.

If you haven't set up SSH yet, go find a monitor & keyboard.  There's no way to set up what you want without SSH from a default Dapper install (as far as I'm aware).

---

### Post by brickbat on 2006-07-31
Oh.  I didn't set up SSH.

Thanks for the advice.

---

