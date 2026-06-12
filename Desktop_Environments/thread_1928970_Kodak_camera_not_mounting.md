---
title: "Kodak camera not mounting"
date: 2012-02-21
forum: Desktop Environments
---

### Post by 3djake on 2012-02-21
Hi, in ubuntu this camera would just show up on the desktop just like a usb drive, in xubuntu it does not.

I tried it on my mothers laptop and on my own, they are both runnin xubuntu 11.10 and i would like to get it working for her.
[B]
lsusb[/B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 040a:0578 Kodak Co. CX7300/CX7310

**gvfs-mount -l**
Drive(0): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): STAR_WARS_EPISODE_VI
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
Volume(0): KODAK EasyShare CX7300 Digital Camera
  Type: GProxyVolume (GProxyVolumeMonitorGPhoto2)
Volume(1): KODAK EasyShare CX7300 Digital Camera
  Type: GProxyVolume (GProxyVolumeMonitorGPhoto2)
[B]
dmesg | tail -20[/B]
[  177.188131] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  177.188134] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  177.188138] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  177.188141] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  177.188144] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  177.188147] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  177.188151] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  177.188154] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  177.188157] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  177.188161] cfg80211: World regulatory domain updated:
[  177.188164] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  177.188167] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.188171] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  177.188174] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  177.188177] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  177.188181] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  189.072046] wlan0: no IPv6 routers present
[  299.956130] usb 3-2: new full speed USB device number 3 using uhci_hcd
[  324.056105] usb 3-2: USB disconnect, device number 3
[  575.960105] usb 3-2: new full speed USB device number 4 using uhci_hcd

thanks for any help in advance

---

### Post by 3djake on 2012-02-22
I still need help with this.

Is there a way to make xubuntu treat it like it was a USB drive like older versions of ubuntu.

Thanks

---

### Post by winh8r on 2012-02-22
I cannot guarantee that this will work but it is worth a try, I have used it on a digital camera before which refused to show up when plugged in.

switch on camera

plug into a different USB port than you normally use (swap your USB devices around in their ports)

once it is plugged in, restart the computer

As the system boots it will detect the USB Mass Storage Device and it should appear on the desktop as such.

Failing the above , try taking the memory card out of the camera and either putting it in another device (does not matter what device) and connect it that way.

I have used a SatNav to access a memory card from a Fuji camera that had a damaged usb outlet and get the images into a computer.

Or go the simple route and plug the card into the PictBridge on you printer if you have one.

Hope there is either a solution here or at very least some inspiration!!!

---

### Post by LewisTM on 2012-02-22
The drive should show up on your desktop and on Thunar's left pane.
If you go the the Settings Manager/Removable Drives and Media/Storage tab, the first two options should be enabled, the rest is up to you.
Hopefully that's your problem 'cause I don't think I can help you further.
Does connecting other USB storage work, like a flashdrive?
Is the camera accessible in /media?

---

### Post by 3djake on 2012-02-23
> **winh8r said:**
> 

plug into a different USB port than you normally use (swap your USB devices around in their ports)

once it is plugged in, restart the computer

As the system boots it will detect the USB Mass Storage Device and it should appear on the desktop as such.


thanks but I tried it on 2 laptops

> **winh8r said:**
> 
Failing the above , try taking the memory card out of the camera and either putting it in another device (does not matter what device) and connect it that way.


Thanks but that does not really solve the problem and its not really ideal for my mother, the camera also uses internal memory and she would have to go get the Navman from the car and then borrow a cable off me to connect it to the laptop.

> **LewisTM said:**
> The drive should show up on your desktop and on Thunar's left pane.
If you go the the Settings Manager/Removable Drives and Media/Storage tab, the first two options should be enabled, the rest is up to you.
Hopefully that's your problem 'cause I don't think I can help you further.
Does connecting other USB storage work, like a flashdrive?
Is the camera accessible in /media?

Thanks but its not mounting and yes other USB devices such as my mp3 player, 100gb usb hard drive and my caanoo all mount and open up in thunar automatically.


Would really like to get this working, looking at the output from **gvfs-mount -l** that says *GProxyVolumeMonitorGPhoto2*, this is what I think is causing the problem, I think if there is a way to make it*GProxyVolumeMonitorGdu* it will mount properly.

Some one is bound to see what is going on here lol.

Thanks for any help in advance.

---

### Post by winh8r on 2012-02-23
try this :

```
sudo apt-get install digikam
```

plug camera in

select view mode and it should allow you to import photos.

I think digikam is fairly good at recognising Kodak cameras for some reason.

---

### Post by LewisTM on 2012-02-23
> **winh8r said:**
> I think digikam is fairly good at recognising Kodak cameras for some reason.
I was about to suggest something similar, only using gThumb which works well in Xfce.

I think your problem is that your camera is recognized ... as a camera and not as a filesystem. It would use a different transfer protocol.

If either gThumb or digikam work, you can set Thunar to open them upon connecting your camera.

For the daring, there is this package, gphotofs, that would enable you to mount the camera as a filesystem.

---

### Post by winh8r on 2012-02-23
> **LewisTM said:**
> I was about to suggest something similar, only using gThumb which works well in Xfce.

I think your problem is that your camera is recognized ... as a camera and not as a filesystem. It would use a different transfer protocol.

If either gThumb or digikam work, you can set Thunar to open them upon connecting your camera.

For the daring, there is this package, gphotofs, that would enable you to mount the camera as a filesystem.


Seems that digikam uses gphoto2 as a base and on looking here:

[http://www.gphoto.org/]("http://www.gphoto.org/")

at the revisions, they seem to have added support for a huge amount of digital cameras over the years, many more than I have previously found on any other application.

So either gphoto2 or digikam look like the best bet for anyone having similar issues where the camera is seen but not accessed.

I hope this is of some help to the OP and anyone else in a similar situation.

---

### Post by LewisTM on 2012-02-23
FYI gThumb also uses the gphoto2 library.

---

### Post by cottfcfan on 2012-02-23
I had the same problem with a Kodak Easyshare DX4530.
Just installing Shotwell worked.
The camera showed up in the Left hand column, and I just imported the pictures to my collection.

---

### Post by 3djake on 2012-02-23
Thanks but xubuntu comes with gThumb and the gphoto2 libraries pre installed.

Its just so frustrating, I remember it using the same camera earlier versions of ubuntu (7.10, I think it was) with out having to do anything to get it to work.

I will see my mother tonight, I will try digikam tho, maybe it adds its own libraries as well as using gphoto2's.
Thanks

---

### Post by cottfcfan on 2012-02-24
3djake,
GThumb may well come installed with gphoto2 libraries, but it does'nt recognize my Kodak Camera, where Shotwell does.
Try it, you have nothing to lose, you can always uninstall it if it doesn't work.

ps.. The problem with installing Digikam, is that it will drag half the KDE Desktop in with it as well.

---

### Post by WinRiddance on 2012-05-26
Experienced similar problems with my Nikon 100. Xubuntu 11.10 mounted everything just fine, upgraded to Xubuntu 12.04 and couldn't get the camera to mount, no matter what I tried. Even switched file managers (Nautilus & PcmanFM) but those wouldn't even automount my external disks.

So I went back to Thunar, got rid of all of my image viewing/camera related image apps., and started clean with only Gimp for image manipulations/designing, EOG (Eye of Gnome) which is my preferred basic image viewer, and Shotwell ... which did indeed recognize & mount my camera. Edited the path and automount in Shotwell, and now my imports take place automatically when I plug the camera into the USB port.
Tried several others too ... hated Digikam ... definitely like Shotwell. :)

.

---

