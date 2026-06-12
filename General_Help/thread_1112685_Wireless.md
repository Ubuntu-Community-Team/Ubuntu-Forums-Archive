---
title: "Wireless"
date: 2009-03-31
forum: General Help
---

### Post by brampt1 on 2009-03-31
Hi,
Need help getting the D-link wireless desktop adapter to work, model # dwa-542. 
Thanks

---

### Post by RedSingularity on 2009-03-31
Post the output of lspci when put into the terminal.

---

### Post by brampt1 on 2009-03-31
> **Shadow121 said:**
> Post the output of lspci when put into the terminal.


00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
01:02.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


Thanks for the help

---

### Post by RedSingularity on 2009-03-31
You need drivers to atheros.  Try [THIS](http://sourceforge.net/projects/madwifi/).  Let me know if that works or not.  Do you need help installing?

---

### Post by brampt1 on 2009-03-31
> **Shadow121 said:**
> You need drivers to atheros.  Try [THIS](http://sourceforge.net/projects/madwifi/).  Let me know if that works or not.  Do you need help installing?

Hi,
I downloaded madwifi-0.9.4 to my desktop, not sure how to install it.
Thanks :)

---

### Post by RedSingularity on 2009-03-31
Ok make sure you get the tar.gz file.  Extract the file to the desktop.  In terminal type cd ~/Desktop/madwifi-0.9.4

Then type ./configure
Then type make
Then type sudo make install

Try that.....

---

### Post by RedSingularity on 2009-04-01
I'm sorry, forget the ./configure and the make install.  You should just need to type make into the terminal for that part.

---

### Post by brampt1 on 2009-04-01
> **Shadow121 said:**
> Ok make sure you get the tar.gz file.  Extract the file to the desktop.  In terminal type cd ~/Desktop/madwifi-0.9.4

Then type ./configure
Then type make
Then type sudo make install

Try that.....


Thanks      :)

---

