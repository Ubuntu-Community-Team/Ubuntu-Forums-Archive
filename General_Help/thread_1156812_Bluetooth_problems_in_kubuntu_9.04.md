---
title: "Bluetooth problems in kubuntu 9.04"
date: 2009-05-12
forum: General Help
---

### Post by Morientes on 2009-05-12
I have some problems with bluetooth in kubuntu 9.04.
I have tried connecting two different phones (to use as remote) but kubuntu does not see any of them. They both work fine in Windows.
I get this error in my messages:
```

[   91.181522] bluetoothd[3484]: segfault at 7 ip b7cebdc3 sp bff535f4 error 4 in libc-2.9.so[b7c7c000+15c000]

```
I tried starting bluetoothd manually but it doesn't seem to help.
Are there any known problems with bluetooth? Anyone know what I can do to fix it?

---

### Post by Morientes on 2009-05-19
Anyone?

---

### Post by Kevbert on 2009-05-19
Have you made the phones visible to the PC ?
Is powersave on the phone off ? (especially for Ericsson/SonyEricsson phones).
If you go into Konsole and enter
```
hcitool scan
```
do you get anything displayed ?

There seem to a number of problems when using bluetooth where it segfaults. Please take a look at [[COLOR="Red"]this[/COLOR]]("https://launchpad.net/+search?field.text=bluetooth+segfault").

---

### Post by Morientes on 2009-05-20
The phones are visible and powersave is off.

hcitool just gives me:
```

Scanning ...
Inquiry failed: Connection timed out

```

It's damn annoying. I used to use my phone to control mythtv and it worked really well, but since Ubuntu 8.10 it hasn't worked at all.

---

### Post by Kevbert on 2009-05-20
This error must have occurred since release as 9.04 Alphas worked fine. I've just gone back and tried Kubuntu 9.04 latest release and am now getting the errors
```
2009-05-20 18:15:15	kevin-dt1b	bluetoothd[2807]	Connection refused (111)
2009-05-20 18:16:24	kevin-dt1b	bluetoothd[2807]	File descriptor in bad state
```
in system log. What is happening is that as soon as I try to connect and pair the phone and PC, they connect and then disconnect within a second.  I'll raise another bug report on this and see what happens. I'll also recheck on 9.04 Ubuntu just in case that's broken again. Bluetooth is flaky again!!!
Bug report is [COLOR="Red"][here.]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/378775")[/COLOR]
Ubuntu 9.04 partly works as I can browse files on the phone, but still not send files to the phone (covered by another bug report).

---

### Post by Morientes on 2009-05-21
Ok, good that others are having problems and not just me, hehe.

Mine actually never connects to the phone. As far as I can tell it does not see it at all.

---

### Post by Kevbert on 2009-05-22
Have you seen [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/BluetoothRemoteControl") ?
There are a number of articles on bluetooth in the community pages.

---

### Post by Morientes on 2009-05-22
Thank you for the link!
But I can't use it right now I guess, since bluetooth appears completely broken.

---

### Post by growled on 2009-05-22
Funny, Bluetooth works perfectly for me in Kubuntu. It has crashed once but nothing bad other than that. That doesn't help you at all, I know. 

Of course, I always go back and add nearly everything I can find in the repository on bluetooth and bluez and obex.

---

### Post by Lucretia9 on 2009-08-14
Bluetooth is broken here. According to /var/log/messages, bluetoothd keeps segfaulting, sometimes when adding the dongle and sometimes when removing it. The /etc/init.d/bluetooth script also doesn't load the bcm203x module (mine is a Broadcom BCM92035DGROM according to lsusb -vv).

Just to give you an idea of the log:

Aug 14 10:12:57 rogue kernel: [35227.560532] usb 7-2: USB disconnect, address 2
Aug 14 10:12:57 rogue kernel: [35227.563072] bluetoothd[12162]: segfault at 100000007 ip 00007f806a10c629 sp 00007fff72f80fd0 error 4 in libc-2.9.so[7f806a094000+168000]
Aug 14 10:13:01 rogue kernel: [35230.996029] usb 7-2: new full speed USB device using uhci_hcd and address 3
Aug 14 10:13:01 rogue kernel: [35231.181807] usb 7-2: configuration #1 chosen from 1 choice
Aug 14 10:13:19 rogue kernel: [35249.384549] usb 7-2: USB disconnect, address 3
Aug 14 10:13:22 rogue kernel: [35252.628049] usb 7-2: new full speed USB device using uhci_hcd and address 4
Aug 14 10:13:23 rogue kernel: [35252.823091] usb 7-2: configuration #1 chosen from 1 choice
Aug 14 10:14:01 rogue kernel: [35291.356130] bluetoothd[28867]: segfault at 100000007 ip 00007f26ef188629 sp 00007ffff7ffae80 error 4 in libc-2.9.so[7f26ef110000+168000]

That's a disconnect, reconnect, disconnect, reconnect.

I'm on Ubuntu (GNOME), the Bluetooth icon only appears every now and then, it won't scan, it mostly won't give me anything, I've managaged to get the MAC address and that's about it.

Bluetooth for me was broken in Hardy (my last version) too and I used different packages to get it to work.

Luke.

---

