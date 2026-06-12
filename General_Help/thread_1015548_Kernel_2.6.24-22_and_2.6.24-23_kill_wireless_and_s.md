---
title: "Kernel 2.6.24-22 and 2.6.24-23 kill wireless and sound"
date: 2008-12-18
forum: General Help
---

### Post by Akeldama on 2008-12-18
I'm running 8.04 Hardy on a Dell Inspiron 2200 laptop. The recent kernel updates to 22 and 23 both disable my wireless and sound. By accessing the Grub boot menu and selecting 2.6.24-21, all is well again.

Suggestions?

Akeldama

---

### Post by markwend on 2008-12-20
I can confirm the same problem on a HP pavilion dv6700 running bcmwl5 broadcom wireless driver through ndiswrapper. 

With the latest kernel update, the wireless light is off and I'm unable to connect. When I boot off the previous kernel, wireless is enabled again.

Seems like a serious problem in the latest kernel update!

---

### Post by zarg@henrikke on 2008-12-20
> **Akeldama said:**
> I'm running 8.04 Hardy on a Dell Inspiron 2200 laptop. The recent kernel updates to 22 and 23 both disable my wireless and sound. By accessing the Grub boot menu and selecting 2.6.24-21, all is well again.


I have swapped back to using 2.6.24-21 too. On my HP nc6400 laptop, recent kernels seem to have more problems with Hilbernate/Wireless combo.

---

### Post by Akeldama on 2008-12-20
> **Akeldama said:**
> I'm running 8.04 Hardy on a Dell Inspiron 2200 laptop. The recent kernel updates to 22 and 23 both disable my wireless and sound. By accessing the Grub boot menu and selecting 2.6.24-21, all is well again.

For further clarification and information:

Sound:
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

Wireless:
Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Akeldama

---

### Post by markwend on 2008-12-21
Today's restricted modules update, addressing broadcom driver-related kernel panics, has fixed the problem for me.

---

### Post by dridle on 2008-12-24
> **Akeldama said:**
> I'm running 8.04 Hardy on a Dell Inspiron 2200 laptop. The recent kernel updates to 22 and 23 both disable my wireless and sound. By accessing the Grub boot menu and selecting 2.6.24-21, all is well again.

Suggestions?

Akeldama

Same problem with 22, ibm thinkpad t20.

---

### Post by Mujaheiden on 2009-02-15
...same on a Thinkpad R32, after upgrading from 7.10 to 8.04 with soundcard I82801CAICH3 and WiFi AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

Ill consider further upgrading to 8.10...

---

