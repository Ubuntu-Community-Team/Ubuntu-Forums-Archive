---
title: "Sun VirtualBox Full Screen"
date: 2009-05-01
forum: General Help
---

### Post by hacko on 2009-05-01
I have Windows Vista and i cant get full screen with the ubuntu(9.04).
I can only get 800x600 and i have 1440x900 screen :S

Thx :)

---

### Post by Legace on 2009-05-01
**For Ubuntu host: (if you are running a virtual Vista machine)**

Have you installed guest additions?
If not open your virtual-Vista, and once you're on the desktop, click “Install Guest Additions” from the "Devices" menu.

[img]http://www.dedoimedo.com/images/computers/2008/virtualbox-install-guest-additions.jpg[/img]

After the install, reboot, and you should be able to resize the VirtualBox window (to any resolution, e.g. 1234x555)


**For Vista host: (if you are running a virtual Ubuntu machine)**
[http://tombuntu.com/index.php/2008/05/23/install-virtualbox-additions-for-an-ubuntu-804-guest/](http://tombuntu.com/index.php/2008/05/23/install-virtualbox-additions-for-an-ubuntu-804-guest/)

---

### Post by lls666 on 2009-05-11
i have the same problem...

jaunty host, winxp guest...
had more resolution options before installing guest additions... after the installation the system just gives me 800x600....

anyone??

also have problems attaching usb drives and connecting the guest to the net... shared folders seem to work though :D

---

### Post by tuxxy on 2009-05-11
> **lls666 said:**
> i have the same problem...

jaunty host, winxp guest...
had more resolution options before installing guest additions... after the installation the system just gives me 800x600....

anyone??

also have problems attaching usb drives and connecting the guest to the net... shared folders seem to work though :D

You do not use Windows to resize, use your mouse and drag the corner of the Virtualbox window to the desired size.

---

### Post by lls666 on 2009-05-11
cool :)
and thanks for the quick answer...

can you also point me in the right direction regarding
- internet access (ubuntu host is connected via wireless... guestxp isn't able to connect but sharedfolders work even though only one way)
- usb drives aren't recognized by the guest. added a filter and set the access to `any` but didn't help

---

### Post by tuxxy on 2009-05-17
Did you install the PUEL version

---

### Post by lls666 on 2009-06-04
after a long time I had to wipe out my windows and gave ubuntu a clean install as well and reinstalled Virutalbox... turns out that I didn't know how to use the group settings of Ubuntu...

if anyone reads this thread here are the instructions:

get the *.deb file from Sun's website,
there is a popup at the end of the installation that actually warns you about the groups, so 
- go to System->Administration->Users and Groups
- click Unlock 
- double click your username
- go to User Privileges tab 
- select Use Virtualbox at the bottom and exit

now USB will work in Virtualbox... just click on the USB icon on the Virtualbox frame (or use the dropdown menu at the top), select the USB you want to use. The device will be unmounted from Ubuntu and mounted in the guest OS

!!! make sure to either shutdown the guest OS or `safely remove` the device before plugging it out. I read in some of the help files that data will be lost / corrupted if you don't... (i believe the possibility is higher in that kind of setup as opposed to just unplugging from Windows... IIRC Virtualbox doesn't actually record the files to the USB device (talking about sticks and mass storage devices obviously) but keeps them in a temporary folder or so... so if you unplug w/o safely removing the temporary files are dumped...)

---

