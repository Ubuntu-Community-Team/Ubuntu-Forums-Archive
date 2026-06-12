---
title: "Recognising Scanner on xsane"
date: 2012-04-09
forum: Desktop Environments
---

### Post by Geffers on 2012-04-09
Hi people,

I have a home network with various devices connected.

One is a very old computer (AMD 350) which is used merely as a printer scanner server and file server. I do not now have a monitor connected to this computer as I just switch on; I know it halts at the log in screen but all my requirements work at this stage, shutdowns are done via Ctrl-T, D, Ctrl-D so are done properly.

Any tweaks are done via an network ssh log in screen.

Xsane, via the network, sees my Multi-Function HP printer which works fine but my old Epsom 1200u Perfection scanner is not seen.

I get the following output from sane commands;

```
sane-find-scanner

found USB scanner (vendor=0x03f0 [HP], product=0x5d11 [Photosmart C5200 series]) at libusb:001:004
found USB scanner (vendor=0x04b8, product=0x0104) at libusb:001:003
```

```
sudo scanimage -L

device `epson:libusb:001:003' is a Epson Perfection1200 flatbed scanner
device `hpaio:/usb/Photosmart_C5200_series?serial=MY781DC2GS0559' is a Hewlett-Packard Photosmart_C5200_series all-in-one
```

Without sudo only the HP device is found.

I am struggling a bit here as I can only use command line so I would appreciate any pointers to get my Epson scanner recognised.

Geffers

---

### Post by Charlotte18 on 2012-04-09
In my opinion, you need to edit the following file:

/lib/udev/rules.d/40-libsane.rules

Go to the terminal and type:

```
gksu gedit /lib/udev/rules.d/40-libsane.rules
```

When the file opens, go to the end of the vendor list (not the end of the file, just the end of the vendor list) and add these lines:

```
# Epson Perfection 1200U
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0104", ENV{libsane_matched}="yes"
```

Restart the computer and see if the Epson scanner works without your being root. If it still doesn't work, erase the product id from the lines above (ATTRS{idProduct}=="0104") so that they read:

```
# Epson Perfection 1200U
ATTRS{idVendor}=="04b8", ENV{libsane_matched}="yes"
```

Then restart the computer and see if the Epson scanner works without your being root.

---

### Post by Geffers on 2012-04-10
> **Charlotte18 said:**
> In my opinion, you need to edit the following file:

/lib/udev/rules.d/40-libsane.rules

 the computer and see if the Epson scanner works without your being root.

Thanks Charlotte,

Did that on my laptop but no luck.

Were your suggestions for the computer connected to the scanners, if so it doesn't have the rules.d folder.

Geffers

---

### Post by Charlotte18 on 2012-04-10
> **Geffers said:**
> Were your suggestions for the computer connected to the scanners, if so it doesn't have the rules.d folder.
Yes. What is the Ubuntu version number installed on the computer connected to the scanners?  In some earlier versions of Ubuntu, the rules.d folder is inside /etc/udev/. Also, the 40-libsane.rules file above could be called 50-udev-default.rules, 40-basic-permissions.rules, or 45-libsane.rules, depending on the version number of Ubuntu. What is your version number?

---

### Post by Geffers on 2012-04-11
> **Charlotte18 said:**
> Yes. What is the Ubuntu version number installed on the computer connected to the scanners?  In some earlier versions of Ubuntu, the rules.d folder is inside /etc/udev/. Also, the 40-libsane.rules file above could be called 50-udev-default.rules, 40-basic-permissions.rules, or 45-libsane.rules, depending on the version number of Ubuntu. What is your version number?

I think the version is Hardy Heron, the kernel is 2.6.24-27

The rules.d folder is at etc/udev but it didn't have the 40-libsane.rules

As I am not too au faux with editing files vie the command line I just copied the 40-libsane.rules file with the alterations you suggested  on my laptop to the other computer.

Still can't see the epson scanner, scanimage -L doesn't show it but sudo scanimage -L does.

The lack of monitor on the old computer is causing me the main problem.

Geffers

---

### Post by Charlotte18 on 2012-04-11
In my opinion, in Hardy Heron you should edit the following file:

/etc/udev/rules.d/40-basic-permissions.rules

In the "USB devices" section of that file, change "0664" to "0666".

The original section will look like this:
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",                MODE="0664"

```

The edited section will look like this:
```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device",                MODE="0666"
```

Save the changes. Remove the file that you copied earlier. Then restart the computer and check whether the Epson scanner works without your being root.

---

### Post by Geffers on 2012-04-12
Charlotte,

Re your suggestion to alter the USB reference, my USB Hewlett Packard multi function printer scanner is working fine from the adjoining USB port.

Geffers

---

### Post by Charlotte18 on 2012-04-12
Changing the number "664" to "666" has nothing to do with the physical USB ports. It changes the *permissions* for USB devices.  "664" gives only the owner read/write permissions. "666" gives everyone read/write permissions. 

Make the changes that I describe above for Hardy Heron. Save the changes. Remove the file that you copied earlier. Then restart the computer and check whether the Epson scanner works without your being root.

---

### Post by Geffers on 2012-04-12
> **Charlotte18 said:**
> Changing the number "664" to "666" has nothing to do with the physical USB ports. It changes the *permissions* for USB devices.  "664" gives only the owner read/write permissions. "666" gives everyone read/write permissions. 

Make the changes that I describe above for Hardy Heron. Save the changes. Remove the file that you copied earlier. Then restart the computer and check whether the Epson scanner works without your being root.

Charlotte,

You are brilliant, how do you know all this...
sane starts I get a choice of which scanner to use.

It is working now but why did my original USB Hewlett Packard device work OK.

Now, when Xsane starts I get a choice of which scanner to use.

Thank you very much.

Geffers

---

### Post by Charlotte18 on 2012-04-12
You're welcome. Glad it works now.
> **Geffers said:**
> why did my original USB Hewlett Packard device work OK.
Some devices and brands are supported properly. Others aren't.

Please edit this thread as "SOLVED" in your original post because the principles here of adding the device to 40-libsane.rules or of altering 40-basic-permissions.rules will apply for anyone else who searches for a solution for a scanner that only works as root.

---

### Post by Geffers on 2012-04-13
> **Charlotte18 said:**
> 

Please edit this thread as "SOLVED" in your original post 

Done, once again many thanks.

Haven't used the Epson for years but it has a light box and can scan different sized negatives and slides, something my HP multi function can't do.

Geffers

---

