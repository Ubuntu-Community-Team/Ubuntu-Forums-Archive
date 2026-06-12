---
title: "iRiver iFP device not found. iRiverT30"
date: 2005-10-24
forum: Desktop Environments
---

### Post by felixdzerzhinsky on 2005-10-24
I am trying to get my iRiver T30 working. Can anybody give me a clue?

pjharper@ren0:~$ sudo ifp firmupdate /usr/local/src/T30_MTP.HEX
Password:
iRiver iFP device not found.
Note: Please check USB connection.
pjharper@ren0:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 4102:1119 iRiver, Ltd.
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 003: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by hajk on 2005-10-25
Are you connecting the USB cable in the right order? As I understand it:
1. Plug USB cable into computer.
2. Switch iRiver player on, then insert cable into player, display confirms that 
    USB connection has been established.

---

### Post by bionnaki on 2005-10-25
I have an iriver h340 (which rules btw). firmware updates are done from within the player itself - just copy the .hex file over to the root directory of the player & "update firmware" option in the control panel.

the iriver just plugs in via usb as an external harddrive.

---

### Post by Hairy_Palms on 2005-10-25
yea most irivers show up as external hard drives, no software needed, are you by any chance using the wind-up seat-belt-type cable that came with it? it sucks, it doesnt connect properly use a different usb cable.

---

### Post by felixdz on 2005-10-25
This one isn't even showing up on my windoze partition. "Plays for Sure!":mad: 

I'll try  it on my girlfriends computer tonight. Starting to think its not good..

---

### Post by bionnaki on 2005-10-25
so, whats happening when you plug it in?

I know with my h340, there is a setting from within the player that'll change what happens when the player is plugged in - it will either charge or it'll just connect for browsing.

have you visited [http://www.misticriver.net/forums.php](http://www.misticriver.net/forums.php) ?

---

### Post by felixdz on 2005-10-27
Well it worked on my girlfriends computer. I have a few songs on it in horror of horrors wmv format!

It appears it is an MTP player that works with Windoze media player.  I understand that I need to upgrade the firmware to make work as a UMS device. Can anybody point me to a simple doc that explains this for the T30?

Thanks for those who have replied so far.

---

### Post by bionnaki on 2005-10-27
no idea
visit the forums, they know everything.

---

### Post by felixdz on 2005-11-06
pjharper@ren0:~$ tail -f /var/log/messages

Nov  6 15:49:24 localhost kernel: [4474126.622000] usb 1-2.3: new full speed USB device using uhci_hcd and address 5

---

### Post by felixdz on 2005-11-06
Using ifp_gui it tells me it is UMS firmware:

pjharper@ren0:~/download$ ./ifp_gui
info: ignoring device with UMS firmware.
ifp Device NOT found
info: ignoring device with UMS firmware.
ifp Device NOT found

---

### Post by bionnaki on 2005-11-06
how are you plugging it in?
on the h340 there are two outputs - media & data.
media doesnt work because
it has something to do with drm
(non-drm music will not transfer or something).
however, the data output works just fine.
does your player have anything like this?

have you been to the forums to ask?

---

### Post by MrSiegal on 2005-11-14
I have the same problem as mentioned earlier about the iRiver T30 on ubuntu. After reading through some threads on the misticriver-forum, I found out that the US and European version can't be used on linux because it's firmware is based on mtp (microsoft "secure" firmware) which ties it as mentioned in an earlier post, to windows media player. Further more iRiver isn't planning to release any ums-firm/software for the t-models, so all in all it seems that we just have to wait and see what iRiver does or someone manages to find a workaround.

---

### Post by felixdz on 2005-12-02
I will never buy another iRiver device. I have to use Windoze to do my music. Hope to sell it and get an iPod.

---

### Post by hajk on 2005-12-02
Sorry to hear that. 

My own experience is much better: iFP-795 with 500MB Flash memory, bought it mainly because it can do MP3 as well as OGG. Just today I upgraded the firmware to the latest UMS-version, player is now recognized as regular USB storage disk. (Note: Windows not needed for upgrade, Breezy package ifp-line can do it... though after the upgrade it can/should no longer be needed.) :D

---

### Post by felixdzerzhinsky on 2005-12-16
I think the problem is with the T30. iRiver really got on the Microsoft DRMA bandwagon. It doesn't work with Mac or Linux. 

Hopefully someone will come up with a hack in time.

I might have another try to get it working this weekend. Has anybody got it to the T30 to go with ubuntu?

---

### Post by crimesaucer on 2006-12-11
Hello, I know this is a little late, but I also have a T30 and have had the same problems.

I updated my firmware to 1.71 ums from 1.71 mtp, when I did this I choose the ums option at the bottom of the dialog box. I used my Windows Xp partition to do this since I was unable to do this using wine.(.Dll files)

here is the link to a page with 4 links that will sort of help you: [http://mtp-ums.net/](http://mtp-ums.net/)

you can get the firmware from there and the iRiver Plus 2 music jukebox that has ogg format as well as mp3, m3u, wav, and others from one of those links too.

When trying to use my xubuntu 6.10 and the usb connection with my iRiver T30 formatted with the 1.71 ums update, was/is difficult. 

It loads songs ripped in ogg format from Sound Juicer perfectly. The format was CD quality, Lossy (ogg multimedia) 

But I didn't like the low bit rate sound of Sound juicer's ogg (141kbps), and switched to Grip for the -q6 (192kbps quality 6) ogg bit rate to rip a CD.

Then I had problems with the ogg files from Grip, and I also had had previous problems with my old mp3 files that I ripped with WMP10, but I had figured it had just been a Windows WMP issue.

The problem that I kept having was that my iRiver T30 can't load those music files in the correct (1-10)order. What I was doing was clicking on the sda icon on my desktop/thunar, and then clicking the /sda/media/usbdisk/ . Then I had created a music folder and had opened it and dragged and dropped music folders into there from my mp3 music folder and my Grip ogg folder. The folders would show in my device but the songs would load in an incorrect order (7,1,2,3,4,5,6,8,9,...for the mp3's and 8,2,1,4,...for the ogg ripped from Grip). Sometimes the transfer would be incomplete and just skip through to the next album. 

Everything except the one Sound Juicer ogg folder was messed up. 

But when I transfered the Grip ogg folders to my Windows Xp Partition, and used the ums supported iRiver plus 2 music jukebox, the folder synced perfectly and sounded better than the .wav(192kbps), .mp3(192kbps), and the Sound Juicer.ogg format (140kbps) that had been on my T30 device.

If you're a music lover then ogg 192kbps is worth the effort.

Right now I am trying to use iRiver Plus 2 with wine, but I have Beryl AiGLX installed on my Intel 910 Celeron m and I am getting this Warning:

libGL warning: 3D driver claims to not support visual 0x5b

I'm trying to find out if this is bad for my computer before I run the program, but for now I finally have a reason to use my dual partition other then utorrent. (I don't use wine for utorrent because I have my Windows TCPIP patched to 50, and configured to net.max_halfopen=40*, and a TCP/IP optimizer boosted to 4000kbps for a T1 cable LAN and with proper configuration it's so much faster than Azureus was on Windows, I haven't even tried bit torrent on Linux yet.)

---

### Post by TGArcher on 2007-05-15
> **felixdz said:**
> I will never buy another iRiver device. I have to use Windoze to do my music. Hope to sell it and get an iPod.

Hey, hey. Don't give up and get a stupid iPod. It really isn't that its an iRiver, and yet it is. There are some that work and some that don't. I know an absolute Linux guru who uses an iRiver clix without a problem. I'll keep searching with you and try to find out as well.

:guitar:

---

