---
title: "Dell E6520 Alps Touchpad problems after upgrade Ubuntu"
date: 2013-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Fuv on 2013-06-07
Hello,
I tryed to switch to a new Ubuntu version, but my touchpad makes  troubles. I use a Dell Latitude E6520 laptop with an Alps touchpad.  Currently I'm on Ubuntu 11.10.

  grep -B 5 mouse /proc/bus/input/devices (under 11.10)
  ```

I: Bus=0011 Vendor=0002 Product=0005 Version=7326 
N: Name="ImPS/2 ALPS  GlidePoint" 
P: Phys=isa0060/serio1/input0 
S:  Sysfs=/devices/platform/i8042/serio1/input/input13 
U: Uniq= 
H:  Handlers=mouse0 event13 
```  
The touchpad works well with 11.10.  Tapping and edge scrolling is going well.
  When I switch to 12.04, 12.10 or 13.04 the touchpad is a bit "jumpy".   I can't exactly tap buttons with the cursor. The sensivity is too high.
  I tryed to modify the kernel or replace the touchpad setting, but without success

grep -B 5 mouse /proc/bus/input/devices (under > 12.04)
```

I: Bus=0011 Vendor=0002 Product=0008 Version=7326 
N: Name="AlpsPS/2 ALPS  DualPoint TouchPad" 
P: Phys=isa0060/serio1/input0 
S:  Sysfs=/devices/platform/i8042/serio1/input/input9 
U: Uniq= 
H:  Handlers=mouse1 event9 
```  
How can I fix this? Is there any way  Ubuntu > 12.04 will recognize my touchpad like 11.10 did?
  I tryed with following, but without success (Tapping was fixed, but edge scrolling wasn't possible anymore):
  ```

sudo modprobe -r psmouse 
sudo modprobe psmouse proto=imps
```

Also the psmouse-alps-dkms driver didnt work for me.
  Thanks!

---

### Post by Fuv on 2013-06-22
Anyone? I tryed everything to fix this bug, but without success :(

---

### Post by jahilton20022 on 2013-08-07
Im having this issue on a latitude e5500, i've tried all variants of Ubuntu with the same issue... i'm unable to use any later versions of ubuntu as a result. :(

---

### Post by luca-formaggia on 2013-08-16
I have the same problem on my Latitude e4310

ubuntu 12.04
uname -a 
Linux minnie 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:18:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Here are the specs of the touchpad
-
I: Bus=0011 Vendor=0002 Product=0008 Version=7326
N: Name="AlpsPS/2 ALPS DualPoint TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse1 event8

---

### Post by Fuv on 2013-09-03
Ubuntu 13.10 also doesnt work for me. Canonical certified my hardware for using it with Ubuntu, but sadly there is no support to fix this problem :(

---

### Post by RLDr on 2013-09-03
I solved this same problem after experimenting with different distributions, finally I settled to Kubuntu 12.04 LTS (i.e. KDE flavour of ubuntu). Please, read the following thread, I think it will help you also.
[http://ubuntuforums.org/showthread.php?t=2080686&p=12760229#post12760229](http://ubuntuforums.org/showthread.php?t=2080686&p=12760229#post12760229)

---

### Post by Fuv on 2013-09-04
@RLDr: Thanks, but this didnt work for me. Kubuntu and Ubuntu are using the same kernel. I tryed already Fedora, Mint, Debian, OpenSuse, ... Kernel 3.0.0-12 (e.g. Ubuntu 11.10) is working for me on all distributions, all Kernels > 3.2 (e.g. (K)Ubuntu 12.04) arent working for me.

---

### Post by jahilton20022 on 2013-10-19
this problem nolonger an issue with 13.10 :) (for me any way)

---

### Post by Fuv on 2013-10-31
> **jahilton20022 said:**
> this problem nolonger an issue with 13.10 :) (for me any way)

Lucky you.
Nothing changed for me, even with the newest kernel.

Did you change anything in your settings or did it work out of the box?

---

