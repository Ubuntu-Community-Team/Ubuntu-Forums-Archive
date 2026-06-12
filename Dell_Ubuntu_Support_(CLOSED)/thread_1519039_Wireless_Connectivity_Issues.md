---
title: "Wireless Connectivity Issues"
date: 2010-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lukebart on 2010-06-27
Hello all,

I'm a total newb at this. Sick of Windows 7 already I installed Ubuntu 10.04 yesterday on my Studio 14z. Most things are working great, but I can't get the wireless to connect. Here's the deal:

1) Activated my Broadcom STA wireless driver.

2) I have a hidden network which I typed in. It's a WPA2 personal. It says I'm connected, but I don't see any signal bars and can't connect to anything. Wired works, but is it just a setting issue or something wrong with the wireless drivers?

-Luke

---

### Post by mikewhatever on 2010-06-27
Could you open Applications->Accessories->Terminal and post the outputs of the following commands:
nm-tool
ps -e | grep nm-applet

---

### Post by lukebart on 2010-06-27
Hey Mike,

Here's what I got:


NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:24:E8:BD:24:72

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1
    DNS:             192.168.1.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:22:5F:C3:F2:EE

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


luke@LukesLaptop:~$ ps -e | grep nm-applet

---

### Post by mikewhatever on 2010-06-28
Right, the lack of output from the second command means nm-applet is not running. Try adding the notification area to the panel:
right click the panel
select 'Add'
select the 'notification area'
click 'Add'

---

### Post by lukebart on 2010-06-28
Hey Mike,

Yeah, I added the notification thing, which looks like three dots right? There was already three dots next to the wireless connection, however.

-L

---

### Post by mikewhatever on 2010-06-28
Well you can always remove the second one, no harm done. Try launching nm-applet from a terminal window. Hopefully, that will provide some useful output.
```
nm-applet &
```

---

### Post by lukebart on 2010-06-29
This is what I received:

nm-applet &
[2] 1595
[1]   Exit 1                  nm app
luke@LukesLaptop:~$ An instance of nm-applet is already running.

** (nm-applet:1595): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

---

### Post by Jonny Two Shoes on 2010-06-30
I fixed my wireless issue on a D610 by deleting the etc/network/interfaces file and rebooting.  Then suddenly the icon to display network connection at the top right came back.  

But beware I'm not very good with Linux yet :P

So if you are also missing the notification icon at the top right you can try open a terminal then type each line and press enter after each:

cd /
cd etc
cd network
sudo rm interfaces

then reboot your pc

Don't know if this will help you.

---

### Post by Jonny Two Shoes on 2010-06-30
Furthermore if you are seeing that icon but just can't connect to anything, well my D610 wireless drivers were not supported in initial install of Ubuntu.  

I had to plug into wired to connect to Internet.  Perform sudo apt-get update command in a terminal and let it finish.  Then go to system/administration/hardware drivers in the menus and download and install a supported driver it automatically picked up.

---

