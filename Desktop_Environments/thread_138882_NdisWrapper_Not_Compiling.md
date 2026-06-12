---
title: "NdisWrapper Not Compiling"
date: 2006-03-02
forum: Desktop Environments
---

### Post by yumigator on 2006-03-02
Hey everyone,

After a bad HD crash, I gave up on my Debian/win2k setup and went to Ubuntu only. So far it looks really cool, but I'm having trouble compiling packages. For example, the [NdisWrapper guide]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Compile_and_install") says I should type
```
#make distclean
#make install
```
after cd'ing to the source directory.

When I do that, I get errors, as seen in the following screenshot:

[IMG]http://img116.imageshack.us/img116/1165/screenshot4bi.png[/IMG]

What's the problem here? What am I doing wrong?

Thanks very much.

EDIT: I don't think this is related, as I haven't even gotten past the compile stage yet, but if it's any help, the card I'm trying to run is a Netgear MA521 (0000:09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180 802.11b MAC (rev 20)).

---

### Post by az on 2006-03-02
[QUOTE=yumigator]H

EDIT: I don't think this is related, as I haven't even gotten past the compile stage yet, but if it's any help, the card I'm trying to run is a Netgear MA521 (0000:09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180 802.11b MAC (rev 20)).[/QUOTE]


Install ndiswrapper-utils and then go to the directory where the .inf file is

type
sudo ndiswrapper -i XXXXX.inf  (XXXX being the file)
sudo ndiswrapper -l
and see if it is installed

sudo modprobe ndiswrapper and you are good to config your connection.  If it works, add
ndiswrapper
to the end of /etc/modules.


You do not have to compile ndiswrapper.   It is included.

---

### Post by yumigator on 2006-03-03
Thanks for your reply, ndiswrapper-utils was successfully installed. I also was able to install the NET8180.INF file. But when I used the -l flag to see if NET8180 was successfully installed, it told me "NET8180 invalid driver!"

What do I do now?

EDIT: Never mind that last question, I didn't know that the .SYS file also had to be extracted also, I thought only the .INF was necessary. Oh well, thanks anyway. Now how would I go about configuring this card to it could connect to the network (I'm using 64-bit WEP encryption)?

---

### Post by az on 2006-03-03
[QUOTE=yumigator]Thanks for your reply, ndiswrapper-utils was successfully installed. I also was able to install the NET8180.INF file. But when I used the -l flag to see if NET8180 was successfully installed, it told me "NET8180 invalid driver!"

What do I do now?

EDIT: Never mind that last question, I didn't know that the .SYS file also had to be extracted also, I thought only the .INF was necessary. Oh well, thanks anyway. Now how would I go about configuring this card to it could connect to the network (I'm using 64-bit WEP encryption)?[/QUOTE]
System - Administration - Networking  - wireless connection.

---

### Post by yumigator on 2006-03-03
All I see under networking is "Ethernet Connection" and "Modem Connection".

---

### Post by az on 2006-03-03
Did you load the module?

sudo modprobe ndiswrapper

If so, show the output of 
tail /var/log/messages
after you load it.  It you made it autoload, post the output of 
dmesg 
after you boot instead.

---

### Post by Ptero-4 on 2006-03-03
And if you ever need to compile anything install build-essential. It install all the basic development tools needed to compile source packages.

---

### Post by yumigator on 2006-03-04
OK, I did dmesg and this is what I got.
```
[4294931.326000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294931.461000] ndiswrapper: driver net8180 (Realtek,10/07/2004,5.173.1007.2004) loaded
[4294931.461000] PCI: Enabling device 0000:09:00.0 (0000 -> 0003)
[4294931.461000] ACPI: PCI Interrupt 0000:09:00.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294931.462000] PCI: Setting latency timer of device 0000:09:00.0 to 64
[4294931.522000] ndiswrapper: using irq 10
[4294932.074000] wlan0: ndiswrapper ethernet device 00:09:5b:8b:c2:19 using driver net8180, configuration file 10EC:8180.5.conf
[4294932.074000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
```

---

