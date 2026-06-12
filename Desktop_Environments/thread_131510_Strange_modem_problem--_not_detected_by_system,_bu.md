---
title: "Strange modem problem-- not detected by system, but will dial"
date: 2006-02-16
forum: Desktop Environments
---

### Post by ladyeldawen on 2006-02-16
After following the handy guide here 
[https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4]("https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4")

 I've managed to get my Intel536 modem installed and able to work, it seems. The problem is that no matter what dialing programs I've used (Networking tool, minicom, wvdial, gnome-ppp), they won't detect the modem in their scans. Only when I specify this device name (per the guide above) "/dev/536ep0" will any of the programs make the modem dial. My problem is that even after going through all the noise and everything, it still won't actually connect to the net. It just stops. I can "talk" to the modem through minicom, and it responds with "ok" to most commands.

 The guide above said to create a SYMLINK in the udev folders called "/etc/udev/rules.d/10-local.rules" to make dialing programs recognize the 536ep0 device as /dev/modem, but I think I might have done it wrong. Any step-by-step guides?

so my problems are: getting system to recognize modem in scan, and getting it to actually connect to the internet. Any help would be most appreciated!

---

### Post by kaamos on 2006-02-16
You can temporarily check if the symlink helps by
```
sudo ln -s /dev/536ep0 /dev/modem
```
and then try the scans etc.

I'm no familiar with udev rules so in that I can't help you much. The idea seems to be
```
sudo gedit /etc/udev/rules.d/10-local.rules
```
and insert
>  # Intelmodem536ep
 KERNEL="536ep0"' SYMLINK="modem"
to make the symlink appear at boot. This of course does not help if the symlink didn't do any good.

---

### Post by ladyeldawen on 2006-02-16
[QUOTE=kaamos]You can temporarily check if the symlink helps by
```
sudo ln -s /dev/536ep0 /dev/modem
```
and then try the scans etc.

I'm no familiar with udev rules so in that I can't help you much. The idea seems to be
```
sudo gedit /etc/udev/rules.d/10-local.rules
```
and insert

to make the symlink appear at boot. This of course does not help if the symlink didn't do any good.[/QUOTE]


No, you did more than enough. Thank you, I'll give those a try. As for the udev rule: I navigated to /etc/udev/rules.d folder, and "10-local.rules" did not exist. How does one go about actually creating that text file. I (probably mistakenly) simply make a new text editor file, saved it on the desktop under the name "10-local.rules", entered the text you gave, and typed

sudo cp 10-local.rules  /etc/udev/rules.d

 I checked in that folder and was successful in trasferring it over. I'll use your command above to check to see if the symlink is effective. Thanks once again.

---

