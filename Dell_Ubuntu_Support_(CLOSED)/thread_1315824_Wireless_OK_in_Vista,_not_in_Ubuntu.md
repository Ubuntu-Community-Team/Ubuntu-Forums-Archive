---
title: "Wireless OK in Vista, not in Ubuntu"
date: 2009-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by OldGrantonian on 2009-11-05
I have a Dell Inspiron 6400 with Vista Home Premium. I've added a dual-boot Ubuntu 9.10 partition.

Wireless works fine with Vista, but not with Ubuntu.

When I enter lspci -nn I get:

Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311]

When I click on the network icon at top right, "Wireless Networks" says "device not ready"

I would be grateful for any advice. (I'm new to Ubuntu.)

---

### Post by vsperez on 2009-11-05
Hi

I have installed BCM412 and it works fine.

Take a look at this page

[http://jomcode.com/fadhil/?p=59](http://jomcode.com/fadhil/?p=59)

and

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

hope it helps

Take

---

### Post by cosine352 on 2009-11-05
in command line 
> /usr/bin/jockey-gtk

check if the driver is listed in the proprietary drivers. If so install it. If it is not there you can just type 
> sudo apt-get install bcmwl-kernel-source


---

### Post by OldGrantonian on 2009-11-06
Thanks to vsperez and cosine352 for useful comments. I've made a big step forward :)

When I tried:

/usr/bin/jockey-gtk

that driver was not in the list. However, I saw "Broadcom STA proprietary wireless driver". The description said it applies to BCM4311, which is what I have.

I installed the driver. Immediately, several wireless connections were available in the connections icon at the top right. My own Orange connection is also available.

I checked in System > Preferences > Network Connections > Wireless tab

There is one entry, for "Auto Orange" connection.

The details also include the correct password (which is a bit scary. It must have found it in the Windows Vista partition.)

Unfortunately, when I try to connect to the connection by providing the password, it simply re-prompts for the password.

I would be grateful for any further advice. I will provide all the technical info from the connection dialog box if required.

---

### Post by OldGrantonian on 2009-11-07
As mentioned in my previous post, the STA driver found all the connections, but the Orange connection does not accept my password. So I'm now trying the instructions given here:

> **vsperez said:**
> 
Take a look at this page

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)



In the README.txt, I'm at the following line:

lsmod  | grep "b43\|ssb\|wl"

I get the result:

ssb                    35300  1 b44
wl                   1272936  0

When I do: 

rmmod ssb

I get the result: 

ERROR: Module ssb is in use by b44

When I do:

rmmod wl

I get the result:

ERROR: Removing 'wl': Operation not permitted

Remembering that I'm an Ubuntu newbie, I would be grateful for any further assistance.

---

### Post by OldGrantonian on 2009-11-07
Everything is now OK. Thanks for help.

---

### Post by efflandt on 2009-11-10
I was just trying to get wireless enabled on Inspiron 6400 from a live 9.10 install iso on USB memory stick (which has a filesystem for persistent data).  This is how I got it to work.

System, Administration, Hardware Drivers
Activate: **Broadcom STA wireless driver** (says you need to reboot)
Reboot hung, so I had to shutdown and cold boot
Didn't work automatically, Hardware Drivers then says it is active, but not in use.
Maybe not necessary, but not sure if the module was mapped, so I did **sudo depmod -a**
then **sudo modprobe -v wl**

It worked.  Although, ifconfig -a shows it as eth2 instead of wlan0.  Hopefully on a normal system it is more automatic once you get it set up, than from an install iso on USB.

PS: wl module did not auto load on booting.  But since ubuntu user auto logs in first, instead of tampering with init scripts I just added following to ubuntu's .profile so if lspci lists BCM4311 and wl is not already loaded, load it (so the USB stick is still portable between different computers):

```
# load Broadcom wireless module if Dell laptop
if lspci | grep -q BCM4311; then
        lsmod | grep -qw wl - || sudo modprobe wl
fi
```

---

### Post by OldGrantonian on 2009-11-11
> **efflandt said:**
> I was just trying to get wireless enabled on Inspiron 6400 from a live 9.10 install iso on USB memory stick (which has a filesystem for persistent data).  This is how I got it to work.
..........



All good advice, thanks. I'm going to try all that :)

---

