---
title: "ps3 controller bluetooth in hardy 8.04"
date: 2008-07-01
forum: Gaming &amp; Leisure
---

### Post by epyon22 on 2008-07-01
I recently got my hands on a ps3 dual shock 3 controller and its been working great connected through usb. Though i would like to have the option of connecting it through bluetooth. I read this thread

[http://ubuntuforums.org/showthread.php?t=609462](http://ubuntuforums.org/showthread.php?t=609462)

the version of bluez utils has changed from 7.10 to 8.04 so this walk through doesnt work.

Does any one know what to do? would the other patch work for the version of bluez utils in 8.04 any help would be apprecated

---

### Post by efj on 2008-07-04
I haven't tried with version 7.10, but I can confirm that it is not working yet with hardy 8.04.

PS3 controller is recognized, paired in Bluetooth, but nothing can be read from the device when launching this command:

> sudo cat /dev/input/js0

That goes for USB and bluetooth.

For the info, my controller is a japanese Dualshock 3.

Any help would be greatly appreciated :-)

---

### Post by epyon22 on 2008-07-05
Oh mine works great using usb. plug it in it just works if i go to system settings in kde and go to keyboards and mice it is registered under the joystick tab. idk if it would be different in gnome. mine is a US dual shock 3

[http://www.pabr.org/sixlinux/sixlinux.en.html](http://www.pabr.org/sixlinux/sixlinux.en.html)
heres the original link if any one wants to see if you can get his fix working your welcome to try it out

---

### Post by swift1337@gmail.com on 2008-07-09
I've actually gotten the Dualshock 3 controller working with Bluetooth in Hardy - in fact, I've gotten two of them working. I essentially followed the steps in the "Bluetooth Pairing" section here:

[https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

However, before the last step, where you start the Bluetooth service, I held down the "Playstation" button until the controller turned off. Once the Bluetooth service started, I turned the controller back on. The Bluetooth widget then asked me to confirm the authentication of the controller, which I did, checking the box that would automatically confirm it in the future. From that point on, the controller worked fine - I've used it in both Super Mario War and pSX without any problems whatsoever.

---

### Post by epyon22 on 2008-07-10
Well that worked so well so simple i had to do what you did and restart my comp and it works fine now. Now im working on figuring out this ps1 emulator in linux :) (usally use psxeven in windows)

---

### Post by efj on 2008-07-10
I managed to have it work.

Here's how I did:

Run the sixpair application to set the bluetooth master in the dualshock
```
./sixpair
```

Stop bluetooth:
```
/etc/init.d/bluetooth stop
```

Discover the new device by running the HIDP daemon
```
killall hidd
hidd --server --nocheck -n
```

**Have the dualshock disconnect from the computer** (no led active anymore ... go to some far away room just to make sure, or shutdown the computer ... your call ;-) ).

Start bluetooth
```
/etc/init.d/bluetooth start
```

**Push the dualshock PlayStation button** in order to activate the connection between the computer and the dualshock.

Then simply set the device as trusted.

I had to reboot once afterwards, then it worked flawlessly.

---

### Post by Gliitch on 2008-07-12
I've managed to setup the ps3 pad, using the sixaxis- working flawlessly :D but does anyone know how to get the sixpair command to boot up at startup? I dont know much about scripts, otherwise id write one. :(

PS: to stop your controller completely, use a pin, on the back to reset it :D that'll shut it off :P 

Gliitch:)

---

### Post by knist on 2008-09-25
Just to be sure. After the initial pairing and setting the pad as trusted, will I be able to connect the dual shock 3 just by pressing the PS-button, exactly like the old non-dual shock sixaxis controller?

According to [http://www.pabr.org/sixlinux/sixlinux.en.html](http://www.pabr.org/sixlinux/sixlinux.en.html) the dual shock 3 might not work in Linux so I just wanted to be sure before I went out and got one. :)

---

### Post by epyon22 on 2008-09-25
yeah works fine its what i used no difference between it and the six axis i still am trying to figure out how to get rumble to work

---

