---
title: "Problem setting up PS3 Controller for Ubuntu 9.10"
date: 2010-03-09
forum: Gaming &amp; Leisure
---

### Post by GameOverDood on 2010-03-09
Hello all,

Sorry if this was the wrong place to ask but I'm trying to get my PS3 (USB wired) controller to work on Ubuntu 9.10. I'm mainly going to use it to work with the PCSX emulator.

I've been following this guide: [https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

I'm stuck at the step that says "c) Run sixpair" under the USB Pairing section. Everytime I input the command...
```
$ sudo ./sixpair
```I get this error message:
```
Current Bluetooth master: 00:1a:80:c4:b5:48
Unable to retrieve local bd_addr from `hcitool dev`.
Please enable Bluetooth or specify an address manually.
```...instead of the supposed result of sixpair echoing.

As far as I know, I've done all the steps up to this point. Help would be appreciated. :)

---

### Post by Supersonic Doom on 2010-12-04
I got this same error when my bluetooth wasn't enabled. Make sure you have enabled bluetooth and then try again, and that hopefully should fix it

---

### Post by doggyollie on 2012-02-23
I had this same problem when trying to connect to my phone.

If you know the address that you would like to change it to use this command in terminal

```
sudo ./sixpair XX:XX:XX:XX:XX:XX
```

where "XX:XX:XX:XX:XX:XX" is blue tooth address of [B]the device that you are trying connect the controller to.

[/B]All thanks to [dbzfanatic ]("http://forum.xda-developers.com/member.php?u=2677253")on xda
[http://forum.xda-developers.com/show...179929&page=21]("http://forum.xda-developers.com/showthread.php?t=1179929&page=21")

---

