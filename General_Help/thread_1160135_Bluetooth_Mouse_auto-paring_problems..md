---
title: "Bluetooth Mouse auto-paring problems."
date: 2009-05-15
forum: General Help
---

### Post by Mihira on 2009-05-15
Hi,
I am having problems to setup auto-pairing for my bluetooth mouse.
First of all this is the only bluetooth device I actually need to auto-pair.
The mouse is working properly, I am using it now. The problem is that everytime I login I have to put the mouse under pairing mode and do ```
sudo hidd --search
```
I have already edited /etc/default/bluetooth to this:
```
HIDD_ENABLED=1
```
and then tried those above:
```
HIDD_OPTIONS="--master --server"
```
```
HIDD_OPTIONS="--server"
```
```
HIDD_OPTIONS="--connect AA:AA:AA:AA:AA:AA --server"
```
```
HIDD_OPTIONS="--master --connect AA:AA:AA:AA:AA:AA --server"
```

None of them worked.
I also edited /etc/bluetooth/hcid.conf adding this:
```
device AA:AA:AA:AA:AA:AA {
name “Microsoft Bluetooth Notebook Mouse 5000”;
}
```
But didn't worked too.

I've been searching the solution for weeks, but all of them use the solutions above. So please don't just say: "Why don't you try Google?".

Anyone have a clue of what I can do?

I am under Ubuntu 8.10 using Microsoft Bluetooth Notebook Mouse 5000.

Thanks,

Mihira

---

### Post by Mihira on 2009-05-16
I don't know if it will help, but some times it shows this when pairing:
```
mihira@mihira-laptop:~$ sudo hidd --search
Searching ...
	Connecting to device AA:AA:AA:AA:AA:AA
Can't create HID interrupt channel: Connection refused

```

It is solved when I turn off and on the mouse.

---

### Post by teddmeister2 on 2009-05-16
Same problem here.  Please someone help!  This is on my wife's computer and if it doesn't work automagically she will just get frustrated.

---

### Post by Mihira on 2009-05-16
> **teddmeister2 said:**
> Same problem here.  Please someone help!  This is on my wife's computer and if it doesn't work automagically she will just get frustrated.
Did you tried the solutions I tried too?

---

### Post by nirdo on 2009-05-17
Same problem with my Microsoft Laser Mouse 8000. I've done everything mentioned above. The most annoying thing to me is what seems to be inconsistent behavior when I get "Can't create HID interrupt channel: Connection refused" after sudo hidd --search  or sudo hidd --connect [addr]. When I switch the mouse off and back on I also get a "host is down" message, then I press the discoverable key on the mouse and usually get the "Connection refused" message

---

### Post by pmenefee on 2009-05-17
Here's what worked for me, thanks to "rustutzman".  The two instructions above the "edit" line fixed it.  The installation of "bluez-compat" may be what you need.  Anyway, it fixed my problem with the MS 5000 on Asus 1000 HE.  Works on restart, too. 

My edit:  I'm using 9.04


> **rustutzman said:**
> Install bluez-compat from the repository. Then run ```
sudo hidd --search
``` It should see your mouse and you'll be good to go.

Russ

edit: I believe Ubuntu NBR has the kernel from [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/) but you might want to look into that also. After I loaded that kernel everything on my 1000he worked. The mouse appeared to pair but didn't. After running the above instruction it successfully paired and now works great.

---

### Post by Mihira on 2009-05-17
> **pmenefee said:**
> Here's what worked for me, thanks to "rustutzman".  The two instructions above the "edit" line fixed it.  The installation of "bluez-compat" may be what you need.  Anyway, it fixed my problem with the MS 5000 on Asus 1000 HE.  Works on restart, too. 

My edit:  I'm using 9.04
I have installed bluez-compat here too...

HEELLLLPPPP

---

### Post by Mihira on 2009-05-30
Nothing yet?
:/

Please, anyone has any idea of what I have to do?

---

### Post by B4R1S3K on 2009-06-02
I have the same problem!

I have tried everthing mentioned earlier, but autoconnection of my Micr. Bluetooth Notebook Mouse 5000 in **Ubuntu 9.04** (Linux Mint 7) don't work.

To connect - I am using "shortcut" with this command:```
 gksudo 'hidd --connect 00:1D:D8:94:A2:45'
```
But there is necessarily to enter password and also set mouse to pairing mode.

Can someone make this procces simpler?

---

### Post by Mihira on 2009-06-07
Well,
one of the last updates just fixed this problem...
and I made it working via the bluetooth applet interface that appears on the tray bar...

:popcorn:

---

### Post by Chronon on 2009-06-27
nevermind.  testing myself.  Thanks!

It worked great for a bit and now it won't auto-detect it after a suspend to RAM.

-----

Seems to have been a fluke.  After rebooting there's no problem.

---

### Post by ubguy900 on 2009-07-30
Hello,

I have a Microsoft Notebook Bluetooth Mouse 5000, and a Dell Latitude D620 laptop with built in Bluetooth.  I can get the device to pair, and even operate correctly.  However, after two minutes the mouse disconnects.  If I move the mouse and click the buttons, it will come back to life after about 10 seconds.  This behavior repeats itself every two minutes.  This renders the mouse unusable for me.  Does anyone know how to correct this?

Using Ubuntu 8.04
Here are some log/messages when it disconnects

Jul 22 21:40:23 pauld-f5laptop kernel: [ 1185.487245] usb 1-2.4: new full speed USB device using uhci_hcd and address 19

Jul 22 21:40:23 pauld-f5laptop kernel: [ 1187.896631] usb 1-2.4: configuration #1 chosen from 1 choice

Jul 22 21:40:44 pauld-f5laptop kernel: [ 1208.718065] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2.4/1-2.4:1.0/hci0/acl001DD898287D/input/input17

Jul 22 21:43:04 pauld-f5laptop kernel: [ 1345.882992] usb 1-2.4: USB disconnect, address 19

Jul 22 21:43:04 pauld-f5laptop kernel: [ 1346.359198] usb 1-2.4: new full speed USB device using uhci_hcd and address 20

Jul 22 21:43:05 pauld-f5laptop kernel: [ 1348.741626] usb 1-2.4: configuration #1 chosen from 1 choice

Jul 22 21:43:15 pauld-f5laptop kernel: [ 1358.965204] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2.4/1-2.4:1.0/hci0/acl001DD898287D/input/input18

Jul 22 21:45:09 pauld-f5laptop kernel: [ 1470.726956] usb 1-2.4: USB disconnect, address 20

Jul 22 21:45:09 pauld-f5laptop kernel: [ 1471.201098] usb 1-2.4: new full speed USB device using uhci_hcd and address 21

Jul 22 21:45:10 pauld-f5laptop kernel: [ 1471.393978] usb 1-2.4: configuration #1 chosen from 1 choice

Jul 22 21:45:11 pauld-f5laptop kernel: [ 1473.277583] usb 1-2.4: reset full speed USB device using uhci_hcd and address 21

Jul 22 21:45:12 pauld-f5laptop kernel: [ 1473.631999] usb 1-2.4: reset full speed USB device using uhci_hcd and address 21

Jul 22 21:45:13 pauld-f5laptop kernel: [ 1474.525782] usb 1-2.4: usbfs: interface 0 claimed by usbfs while 'vmware-vmx' sets config #1

Jul 22 21:50:05 pauld-f5laptop kernel: [ 1766.165268] usb 1-2.4: USB disconnect, address 21

Jul 22 21:50:05 pauld-f5laptop kernel: [ 1766.401859] usb 1-2.4: new full speed USB device using uhci_hcd and address 22

Jul 22 21:50:06 pauld-f5laptop kernel: [ 1766.857336] usb 1-2.4: configuration #1 chosen from 1 choice

Jul 22 21:50:11 pauld-f5laptop kernel: [ 1774.553321] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2.4/1-2.4:1.0/hci0/acl001DD898287D/input/input19

Jul 22 21:52:03 pauld-f5laptop kernel: [ 1884.618972] usb 1-2.4: USB disconnect, address 22

Jul 22 21:52:04 pauld-f5laptop kernel: [ 1887.273827] usb 1-2.4: new full speed USB device using uhci_hcd and address 23

Jul 22 21:52:04 pauld-f5laptop kernel: [ 1885.321961] usb 1-2.4: configuration #1 chosen from 1 choice

Jul 22 21:52:14 pauld-f5laptop kernel: [ 1895.583176] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2.4/1-2.4:1.0/hci0/acl001DD898287D/input/input20

Jul 22 21:53:57 pauld-f5laptop kernel: [ 1997.963300] usb 1-2.4: USB disconnect, address 23

Jul 22 21:53:57 pauld-f5laptop kernel: [ 1998.431501] usb 1-2.4: new full speed USB device using uhci_hcd and address 24

Jul 22 21:53:58 pauld-f5laptop kernel: [ 1998.640329] usb 1-2.4: configuration #1 chosen from 1 choice

Jul 22 21:54:08 pauld-f5laptop kernel: [ 2011.450567] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2.4/1-2.4:1.0/hci0/acl001DD898287D/input/input21

---

### Post by Mastermoose on 2011-08-22
> **Mihira said:**
> Well,
one of the last updates just fixed this problem...
and I made it working via the bluetooth applet interface that appears on the tray bar...

:popcorn:
You could give your user the right to run the hidd command without password in the sudoers file and run sudo hidd... on boot instead.

---

