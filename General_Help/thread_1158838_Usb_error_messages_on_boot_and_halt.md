---
title: "Usb error messages on boot and halt"
date: 2009-05-14
forum: General Help
---

### Post by thedud on 2009-05-14
Hello I just installed the new release Ubuntu 9.04 64 bit. I keep getting these error messages on boot and shutdown. 

Here is the dmesg output:

[    4.228014] usb 1-5: new high speed USB device using ehci_hcd and address 3
[   19.340013] usb 1-5: device descriptor read/64, error -110
[   34.556014] usb 1-5: device descriptor read/64, error -110
[   34.772013] usb 1-5: new high speed USB device using ehci_hcd and address 4
[   49.884013] usb 1-5: device descriptor read/64, error -110
[   65.100013] usb 1-5: device descriptor read/64, error -110
[   65.316013] usb 1-5: new high speed USB device using ehci_hcd and address 5
[   75.724013] usb 1-5: device not accepting address 5, error -110
[   75.836013] usb 1-5: new high speed USB device using ehci_hcd and address 6
[   86.244010] usb 1-5: device not accepting address 6, error -110

[  102.232026] usb 4-1: device descriptor read/64, error -110
[  117.472016] usb 4-1: device descriptor read/64, error -110
[  117.712015] usb 4-1: new full speed USB device using ohci_hcd and address 3
[  132.848015] usb 4-1: device descriptor read/64, error -110
[  148.088012] usb 4-1: device descriptor read/64, error -110
[  148.328013] usb 4-1: new full speed USB device using ohci_hcd and address 4
[  158.736015] usb 4-1: device not accepting address 4, error -110
[  158.872020] usb 4-1: new full speed USB device using ohci_hcd and address 5
[  169.280015] usb 4-1: device not accepting address 5, error -110

My computer specs are as follows:
Motherboard = Asus m2r32-mvp
CPU = AMD Athlon 64 X 2 6400+
Video = Sapphire ATI 4870 1gb

I have tried looking into it some and read to remove some usb module, but that didn't solve the problem. All answers are appreciated.

Thanks in advance.

---

### Post by pro003 on 2009-05-14
do you use an usb connected modem? because if you do , its a known bug.

disconnect it before booting the machine and the reconnect...

---

### Post by thedud on 2009-05-14
Thank you for the quick response. No I don't have a usb modem, but I do have an internal card reader that plugs in the motherboards usb pins. Think maybe that would be an issue? I have never had this issue before on previous versions of Ubuntu.

---

### Post by pro003 on 2009-05-14
most likely, that could be an issue in this case... do you have a option in bios to disable this temporarily?

---

### Post by thedud on 2009-05-14
I checked in the bios like you said to do and found out disabling Bios EHCI hand off under advanced => usb => Bios EHCI Hand Off did the trick.

Wish that there was a better way of fixing it though.

Thanks for all of your help.

---

### Post by pro003 on 2009-05-15
ur welcome :)

---

### Post by AtlantaBob on 2009-06-02
This just isn't a valid solution. I can't believe that 9.04 got out the door with this type of junk. [http://ubuntuforums.org/showthread.php?t=1108113](http://ubuntuforums.org/showthread.php?t=1108113)

Can anyone even tell if there's a Launchpad bug report? I've searched for terms and can't seem to find one.

---

