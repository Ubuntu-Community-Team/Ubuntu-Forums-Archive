---
title: "Ubuntu and Radeon X550"
date: 2006-03-16
forum: Desktop Environments
---

### Post by stuntmaster on 2006-03-16
i tried the breezy badger install.
as soon as it goes to start X after install (i persume to run the first time config, where you setup things like screen res and sound detection), it throws an error stating it couldnt find my graphics device, and shortly after quits out to a Ubuntu prompt.

whats the cause and the solution?

i really want to try this, i am newish to linux as in i can use it well, but anything todo with rebuilding kernels im alien to it.


thanks

ben

---

### Post by UbuntuJohan on 2006-03-20
I had the same problem on my new machine.
Here is what I did to get around it.
Login at the prompt you get and type the following command
```
sudo dpkg-reconfigure xserver-xorg
```
In one of the first screens it will ask you what driver you would like to use.
It will have defaulted to ATI scroll down and select VESA instead.
Then continue throughout the "guide".
When it's done type the following command
```
startx
```
I hope this helps if you haven't solved it yet.

Cheers
//Johan

---

### Post by Robocoastie on 2006-03-21
After you have VESA set up download the Linux ATI driver from ati.com and install it. Be sure to read the installation instructions as some things have changed since the last driver and I don't know if the Ubuntu tips has been updated for it.

---

