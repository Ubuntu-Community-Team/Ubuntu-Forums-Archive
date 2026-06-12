---
title: "Executing a shell script when USB drive plugged in?  (udev?)"
date: 2005-10-27
forum: Desktop Environments
---

### Post by OneSeventeen on 2005-10-27
I'm trying to help out my church with finding a way to easily load mp3's of the service to USB-based mp3 players (which we also hope to sell super cheap if we can get them in bulk) without any hastle for non-tech users.

My idea is to have a kiosk set up, maybe with a number pad so they can choose which service to download (if they missed an older one), so here's the steps I'd like the user to take:

[list=1]
[*]Walk up to the kiosk (which is displaying a nice picture/animation/video of the church logo or something)
[*]Stick in any USB drive
[*]Watch the screen change to a menu which allows them to use the number pad/arrows/mouse/whatever to select what service they would like to add.
[*]Copy the service over to the USB drive, and ask the user if they want to add more.  If the user says yes, it goes back to the previous screen.
[*]Unmount the USB device and display a cheesy thank you screen letting the user know they can now remove their USB drive, knowing the service is on it.
[/list]

I'm actually thinking I can do a web page to do most of this, with the server running on the kiosk itself, which would make a full screen GUI very easy, I would just need the Ubuntu box to know to tell the web page "hey, someone plugged in a USB drive, here is the mount point:"
Then the web page (PHP powered) would say, cool, let me look at the USB drive, make sure they have enough room, offer to take off old stuff, and show them what services are available, then move things around.  (Since PHP can execute shell commands, this would be pretty easy)

So the real question:
How do I make Ubuntu trigger a shell script or something when a USB drive is plugged in?

udev?  if so, how?

---

### Post by OneSeventeen on 2005-10-27
I guess I should also ask if it is possible to suppress automagically trying to do things with the contents of a USB disk, so only my script gets executed.  (my script, and whatever it takes to get it mounted)

I don't want a window to pop up asking if I want to add photos to my photo album... since this will be a publically available kiosk.

---

### Post by cwaldbieser on 2005-10-27
[QUOTE=OneSeventeen]I guess I should also ask if it is possible to suppress automagically trying to do things with the contents of a USB disk, so only my script gets executed.  (my script, and whatever it takes to get it mounted)

I don't want a window to pop up asking if I want to add photos to my photo album... since this will be a publically available kiosk.[/QUOTE]
This link should help: [http://linux-hotplug.sourceforge.net/]("http://linux-hotplug.sourceforge.net/")
As far as disabling the normal system responses to plugging in a flashdrive, you can just disable gnome-volume-manager or ivman, depending on whether you are using Ubuntu or Kubuntu.

---

### Post by OneSeventeen on 2005-10-28
Okay, I've found [this](http://marc.theaimsgroup.com/?l=linux-hotplug-devel&m=108129246317363&w=2), which looks like it might be the solution, but I'm still having a few problems with the details.

A brief overview with my questions added:
> If you want to run a script when an usb 
device is connected, you have to create a file in /etc/hotplug/usb with the 
extension username.
so should I just write a script called /etc/hotplug/usb/myscript.oneseventeen ? or /etc/hotplug/usb/myscript.username ?
>  The layout of that file is good documented, but the 
first column has not to be a module name, but it can be the name of the 
script.  When there is a match and the first column is a script and the 
script is found in /etc/hotplug/usb, the script is executed.

As example:

```

/proc/bus/usb/devices
  P:  Vendor=0d96 ProdID=4102 Rev= 1.00
/etc/hotplug/usb/medion.usermap
   medion.sh 0x000 0x0d96 0x4102 0x01000x00 00 0x0000 0x00 0x00 0x00 0x00 0x00 
0x00
/etc/hotplug/usb/medion.sh
  chmod 777 $DEVICE
```

So I guess I'm wondering, do I just need to make a file called /etc/hotplug/usb/oneseventeen.sh
then make a file called /etc/hotplug/usb/oneseventeen.usermap that calls:
oneseventeen.sh with all those 0x000 0x0d96 things?

If so, does this look hard-coded to a specific vendor?  I want this to work with a wide array of USB devices...

(sorry, I left my linux laptop at home so I can't test things just yet, but I wouldn't mind some pointers if any hotplug gurus are around)

---

### Post by cwaldbieser on 2005-10-28
[QUOTE=OneSeventeen]
So I guess I'm wondering, do I just need to make a file called /etc/hotplug/usb/oneseventeen.sh
then make a file called /etc/hotplug/usb/oneseventeen.usermap that calls:
oneseventeen.sh with all those 0x000 0x0d96 things?

If so, does this look hard-coded to a specific vendor?  I want this to work with a wide array of USB devices...

(sorry, I left my linux laptop at home so I can't test things just yet, but I wouldn't mind some pointers if any hotplug gurus are around)[/QUOTE]
That is essentially how I got my flashdrive to auto-mount in Kubuntu back under Hoary.  However, when I upgraded to Breezy, I found that ivman didn't interact with that script so well.  By itself, ivman seemed to do the auto-mounting just fine.

The man page on ivman goes into some detail about how you can configure it to perform custom actions when a device is plugged in.  Maybe that is the route you should take.
Here is a link to the ivman wiki: [http://ivman.sourceforge.net/]("http://ivman.sourceforge.net/")

---

### Post by JohnBoyDoe on 2005-11-01
Hi,

under Breezy the hotplug udev things changed. The most wikis and Howtos are no longer usefull for breezy

You have to create udev rules in

/etc/udev/rules.d/011_own.rules

The name is not that important unless it has to be the lowest in alphabetical order.
The solution is to use the RUN+ key in the udev rules.

#For a Hp Laserjet it works like this

BUS="usb", SYSFS{idVendor}="03f0", SYSFS{product}="hp LaserJet 1000",NAME="usb/%k", SYMLINK="hplj1000", RUN+="/etc/hotplug/usb/hplj1000"

This rule loads up the firmware. Any other script can be performed. 

This udev rule creates two entries in /dev/  (/dev/usb/lpo the %k adds the name used in the kernel to make it devfs compatibel and /dev/hplj100 as a symlink). 
Just give all USB Devices the same SYMLINK and then it is possible for you to access different Sticks from one these deviecnode names. 

For the various USB drives there must be some a rule that is more "general" perhaps you find this usefull to make your search more precise. I think you can explore the other udev rules to get more infos or hints about handling usb sticks.

When upgrading to newer kernel versions  the udev handling might change again.

HTH
JBD

---

