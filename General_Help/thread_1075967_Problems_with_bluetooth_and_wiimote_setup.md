---
title: "Problems with bluetooth and wiimote setup"
date: 2009-02-20
forum: General Help
---

### Post by eeliottheking on 2009-02-20
ok, so im currently trying to get my wiimote connecting via bluetooth.  I am running ubuntu 8.04 Hardy and using a USB ultra-mini bluetooth 2.0 adapter with EDR to try and connect.  I have successfully gotten this to work with the specified instructions in intrepid on one of my hard drive partitions just fine.

i am following the tutorial here: [https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD)

The needed packages are already installed:

xbmc@xbmc-Media:~$ sudo apt-get install libcwiid1 lswm wmgui wminput
[sudo] password for xbmc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcwiid1 is already the newest version.
libcwiid1 set to manually installed.
lswm is already the newest version.
wmgui is already the newest version.
wminput is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


upon completing this step i do the next task which is scanning for the wiimote ID.  which i get this REGARDLESS of whether or not i am holding 1&2 on my wiimote.

xbmc@xbmc-Media:~$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out

and upon trying to connect to it via Wmgui i get:
xbmc@xbmc-Media:~$ wmgui

I then have it scan for the wiimote and i get:
Bluetooth device inquiry error


so i tried using Xwii, which i got the following with:
xbmc@xbmc-Media:~$ xwii
[1] Tilt Mouse.xwii
[2] classic_controller_p1.xwii
[3] NES Pad.xwii
[4] classic_controller_p2.xwii
[5] toggle_ir.xwii
[6] Nunchuk FPS.xwii
[7] Movie Player.xwii
[8] XMMS-Audacious.xwii
[9] test.xwii
[10] leds.xwii
[11] Frets On Fire.xwii
[12] Nunchuk MAME.xwii
[13] Nunchuk N64.xwii
[14] IR Mouse.xwii
Which profile would you like to use (pick a number)? 9
./xwii "profiles/test.xwii"
Press 1 + 2 to put the Wiimote in discoverable mode.
hci_inquiry: Connection timed out
Failed to connect to any wiimote.
wiiuse v0.12 loaded.
  By: Michael Laforest <thepara[at]gmail{dot}com>
  [http://wiiuse.net](http://wiiuse.net)  [http://wiiuse.sf.net](http://wiiuse.sf.net)
Hold 1 + 2 to put the Wii Remote in discoverable mode.

any ideas?

---

### Post by eeliottheking on 2009-02-20
bump.  im still having no luck

---

### Post by eeliottheking on 2009-02-21
bump

---

### Post by eeliottheking on 2009-02-22
bump

---

### Post by kmac on 2009-02-22
Instead of using 1+2, try using the red button in the battery compartment. In all honesty, I haven't done this in maybe 2 years when I 'built' my HDNES

---

### Post by eeliottheking on 2009-02-22
> **kmac said:**
> Instead of using 1+2, try using the red button in the battery compartment. In all honesty, I haven't done this in maybe 2 years when I 'built' my HDNES

i went through and repeated the same actions with the red btton.  i got the same results as before sadly.  any other ideas?

---

### Post by eeliottheking on 2009-02-22
bump

---

### Post by eeliottheking on 2009-02-22
bump

---

### Post by eeliottheking on 2009-02-22
bump

---

### Post by eeliottheking on 2009-02-23
bump

---

### Post by sr20ve on 2009-02-23
It sounds like ubuntu is having problems communicating with your bluetooth dongle. Have you tried pairing any other devices? Or, I would try another bt dongle.

---

### Post by eeliottheking on 2009-02-23
> **sr20ve said:**
> It sounds like ubuntu is having problems communicating with your bluetooth dongle. Have you tried pairing any other devices? Or, I would try another bt dongle.

unfortunately, i dont have any other blue tooth devices to test this out with; however, i am able to get this running successfully in intrepid using my current dongle and a wii remote.  is this due to intrepid using libbluetooth3?

---

### Post by eeliottheking on 2009-02-23
bump

---

### Post by eeliottheking on 2009-02-23
bump

---

### Post by eeliottheking on 2009-02-24
bump.

sorry for all the bumps, but i see how busy this place gets and i think my topic will get buried if im not a little aggressive.

---

### Post by eeliottheking on 2009-02-24
bump

---

### Post by eeliottheking on 2009-02-25
bump

---

### Post by eeliottheking on 2009-02-26
bump

---

### Post by eeliottheking on 2009-02-27
bump

---

### Post by eeliottheking on 2009-02-28
bump

---

### Post by eeliottheking on 2009-03-02
bump

---

### Post by eeliottheking on 2009-03-02
bump

---

### Post by eeliottheking on 2009-03-04
bump

---

### Post by eeliottheking on 2009-03-04
bump

---

### Post by eeliottheking on 2009-03-05
bump

---

### Post by eeliottheking on 2009-03-05
bump

---

### Post by eeliottheking on 2009-03-06
bump

---

### Post by eeliottheking on 2009-03-08
bump

---

### Post by eeliottheking on 2009-03-09
bump

---

### Post by eeliottheking on 2009-03-10
bump

---

### Post by eeliottheking on 2009-03-10
bump

---

### Post by eeliottheking on 2009-03-11
bump

---

### Post by eeliottheking on 2009-03-14
bump

---

### Post by eeliottheking on 2009-03-15
bump

---

### Post by eeliottheking on 2009-03-18
bump

---

### Post by FreezWay on 2009-08-22
im having the same issues.

---

### Post by dakilla on 2009-10-11
> **eeliottheking said:**
> ok, so im currently trying to get my wiimote connecting via bluetooth.  I am running ubuntu 8.04 Hardy and using a USB ultra-mini bluetooth 2.0 adapter with EDR to try and connect.  I have successfully gotten this to work with the specified instructions in intrepid on one of my hard drive partitions just fine.

i am following the tutorial here: [https://help.ubuntu.com/community/CWiiD](https://help.ubuntu.com/community/CWiiD)

The needed packages are already installed:

xbmc@xbmc-Media:~$ sudo apt-get install libcwiid1 lswm wmgui wminput
[sudo] password for xbmc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcwiid1 is already the newest version.
libcwiid1 set to manually installed.
lswm is already the newest version.
wmgui is already the newest version.
wminput is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


upon completing this step i do the next task which is scanning for the wiimote ID.  which i get this REGARDLESS of whether or not i am holding 1&2 on my wiimote.

xbmc@xbmc-Media:~$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out

and upon trying to connect to it via Wmgui i get:
xbmc@xbmc-Media:~$ wmgui

I then have it scan for the wiimote and i get:
Bluetooth device inquiry error


so i tried using Xwii, which i got the following with:
xbmc@xbmc-Media:~$ xwii
[1] Tilt Mouse.xwii
[2] classic_controller_p1.xwii
[3] NES Pad.xwii
[4] classic_controller_p2.xwii
[5] toggle_ir.xwii
[6] Nunchuk FPS.xwii
[7] Movie Player.xwii
[8] XMMS-Audacious.xwii
[9] test.xwii
[10] leds.xwii
[11] Frets On Fire.xwii
[12] Nunchuk MAME.xwii
[13] Nunchuk N64.xwii
[14] IR Mouse.xwii
Which profile would you like to use (pick a number)? 9
./xwii "profiles/test.xwii"
Press 1 + 2 to put the Wiimote in discoverable mode.
hci_inquiry: Connection timed out
Failed to connect to any wiimote.
wiiuse v0.12 loaded.
  By: Michael Laforest <thepara[at]gmail{dot}com>
  [http://wiiuse.net](http://wiiuse.net)  [http://wiiuse.sf.net](http://wiiuse.sf.net)
Hold 1 + 2 to put the Wii Remote in discoverable mode.

any ideas?

in file: XWii_2.8_source/wiiuse_v0.12/src/io_nix.c
after this at line 172: 
> 	struct sockaddr_l2 addr; line 172 
add on line 173:
	> memset(&addr, 0, sizeof (addr));

shuld look like:
> static int wiiuse_connect_single(struct wiimote_t* wm, char* address) {
	struct sockaddr_l2 addr;
	memset(&addr, 0, sizeof (addr));

	if (!wm || WIIMOTE_IS_CONNECTED(wm))
		return 0;


solved it for me :D

---

### Post by Townley89 on 2010-09-08
Hey, I was having the same problem. I'm not sure if it will work for you, but I realized that my bluetooth device was being occupied by the Bluetooth manager searching for new devices. I closed all windows pertaining to the bluetooth manager/bluez, then reopened WMGUI and it worked :) 

Hope that helps

---

