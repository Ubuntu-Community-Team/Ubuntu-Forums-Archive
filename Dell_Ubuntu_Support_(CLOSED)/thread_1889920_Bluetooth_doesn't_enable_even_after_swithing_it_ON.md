---
title: "Bluetooth doesn't enable even after swithing it ON"
date: 2011-12-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by raghav.venky on 2011-12-02
I use a Dell N5010 with Ubuntu 11.10
I am trying to send a file using bluetooth. I switched it on using the button in the top panel.
But when I click preferences, it say bluetooth is disabled.
It seems that "Bluetooth:On" has no effect on the settings, where there is always on Off.
what should I do?

---

### Post by BC59 on 2011-12-02
On Ubuntu software manager , there are 2 more applications for Bluetooth, BlueWho and Bluetooth Manager, just try them to see if Bluetooth works better with them.

If not try from Synaptic to reinstall the packages about Bluetooth.

---

### Post by raghav.venky on 2011-12-04
I tried both, did not work. I also reinstalled the 'bluetooth' package. Still the same.

The problem is I cannot turn the bluetooth ON in the 'preferences'

As soon as I move the slider to ON, it slides back to OFF automatically

---

### Post by BC59 on 2011-12-04
Try installing this app:

```
sudo apt-get install bluez-utils bluez-firmware
```

Then run:

```
sudo dfutool
```

---

### Post by raghav.venky on 2011-12-04
The what?

---

### Post by BC59 on 2011-12-04
Open a terminal with CTRL+ALT+T and paste inside with SHIFT+CTRL+V the command:

```
sudo apt-get install bluez-utils bluez-firmware
``` Enter and put your password and Enter again.

After the package is installed you can open it running again in the terminal:

```
sudo dfutool
``` Enter

Then follow the instructions.

---

### Post by raghav.venky on 2011-12-05
Installed it. But the dfutool is something about a USB device.  I want to use the Bluetooth in-built in my laptop.

---

### Post by BC59 on 2011-12-05
Then the last resource would be installing the cwiid Wiimote controller package and the lswm Wiimote discovery package:
```
sudo apt-get install wminput lswm
```
Install the drivers (or just reboot):
```
modprobe uinput
```
Run (while pressing button 1/2 on the Wiimote):
```
sudo wminput
```

---

### Post by raghav.venky on 2011-12-06
What's wiimote got to do with bluetooth? Is this a joke?

---

### Post by BC59 on 2011-12-06
Well seems that your Bluetooth device is blocked and I try to unblock it.

---

### Post by celiapgt on 2012-01-05
Please, advise! I'm having the same problem, but I have no WiiMote... in fact, what is that?

---

