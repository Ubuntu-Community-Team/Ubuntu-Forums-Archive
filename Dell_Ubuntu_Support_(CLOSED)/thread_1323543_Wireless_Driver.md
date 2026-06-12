---
title: "Wireless Driver"
date: 2009-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Unstuck on 2009-11-11
I have a n-series 1420 that seems to have lost its wireless driver when upgrading to 9.04.  How do I get it back?

---

### Post by RedSingularity on 2009-11-11
Did you check System>Admin>Hardware Drivers?

If its not there post the output of lspci in terminal.

---

### Post by Unstuck on 2009-11-12
"No proprietary drivers are in use on this system."

LSPCI

> :~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)       
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)                 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)                 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)                
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)                      
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


---

### Post by RedSingularity on 2009-11-12
Apparently that wireless device should work out of the box with ubuntu.  Try this......

In terminal do 

sudo gnome-network-admin

Click Wireless Connection, Click the checkbox by it, then the Properties button.

Fill in the various details of your network. (Note: WPA takes extra software.  WEP works though.)

Decide on manual addressing or DHCP. Click Okay.

Click Wireless Connection, Click the checkbox by it, then the Properties button.

Fill in the various details of your network. (Note: WPA takes extra software.  WEP works though.)

Decide on manual addressing or DHCP. Click Okay.

---

### Post by Unstuck on 2009-11-13
> sudo: gnome-network-admin: command not found
 

That doesn't seem good.

---

### Post by RedSingularity on 2009-11-14
sudo apt-get install gnome-network-admin

Then do what i posted before.

---

### Post by Unstuck on 2009-11-15
I installed gnome-network-admin, but still get the "command not found" response.

> unstuck@unstuck:~$ sudo apt-get install gnome-network-admin
Reading package lists... Done
Building dependency tree
Reading state information... Done
gnome-network-admin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
unstuck@unstuck:~$ gnome-network-admin
bash: gnome-network-admin: command not found
unstuck@unstuck:~$ sudo gnome-network-admin
sudo: gnome-network-admin: command not found


---

### Post by Unstuck on 2009-11-15
The Network Settings doesn't open through terminal, but I can open it through System > Admin > Network.  I should have thought of that earlier...

I entered the SSID and WEP information I found by logging into my router, but it seems I still can't enable a wireless connection.  

The Network Settings asks for ESSID...is this the same as SSID?  If not, where do I find the ESSID?

---

### Post by RedSingularity on 2009-11-15
You shouldnt have to fill that out manually.  Post the output of iwconfig.  That gives info on the wireless card.

---

### Post by Unstuck on 2009-11-15
IWCONFIG
> unstuck@unstuck:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=0 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


Thank you for your help so far, RedSingularity.

---

### Post by RedSingularity on 2009-11-15
No prob  :)

If you are using a notebook make sure your wireless is turned on.  Usually it is a combination of two buttons.  I have researched this and it seems that many have forgot to enable the device.

---

### Post by Unstuck on 2009-11-15
SOLVED!!!  I didn't even know such a button existed!  This has been a problem for months; thank you so much!:popcorn:

---

### Post by RedSingularity on 2009-11-15
LoL....Glad i could help.

---

