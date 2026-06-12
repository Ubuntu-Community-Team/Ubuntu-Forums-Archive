---
title: "LIRC headaches"
date: 2008-12-09
forum: General Help
---

### Post by Aphoxema on 2008-12-09
I've been trying for a while to get LIRC working with my iMON IR receiver I got at best buy. I know it works in Windows fine with the included software.

Before, I was using a serial receiver I made, which I also got working in Windows with WinLIRC, and one time months ago I got it working in Ubuntu but I have no idea how.

If anyone could please tell me where I need to get started, so far I've gotten the LIRC package installed, here's my hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Soundgraph iMON IR/LCD"
REMOTE_MODULES="lirc_dev lirc_imon"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="imon/lircd.conf.imon"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

And when I try to use irw it says
connect: Connection refused

And I have a /dev/lircd but no /dev/lirc0 or anything else.

I'm confident if I can get irw to work and respond to my remotes, I'll be able to handle the rest on my own.

---

### Post by NT4usB on 2008-12-09
Did you try running irw as root?```
sudo irw
```Not a solution but way back in Dapper days, it worked for me and told me I didn't have the correct permissions set for some file or another...

---

### Post by Aphoxema on 2008-12-09
Yes, I have.

---

### Post by laceration on 2008-12-10
How about showing us a 
```
cat /proc/bus/usb/devices
```

---

### Post by Aphoxema on 2008-12-14
It says...

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh=10
B:  Alloc= 13/900 us ( 1%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev= 2.06
S:  Manufacturer=Linux 2.6.27-9-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=00e1 Rev= 0.07
S:  Manufacturer=Microsoft
S:  Product=Microsoft Wireless Optical Mouse&#65533; 1.00
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   6 Ivl=10ms

T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=lirc_imon
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=lirc_imon
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 2.06
S:  Manufacturer=Linux 2.6.27-9-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

---

### Post by laceration on 2008-12-15
```
T: Bus=02 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#= 3 Spd=1.5 MxCh= 0
D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs= 1
P: [COLOR="Red"]Vendor=15c2 ProdID=0043[/COLOR] Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID ) Sub=00 Prot=02 Driver=lirc_imon
E: Ad=81(I) Atr=03(Int.) MxPS= 8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID ) Sub=00 Prot=00 Driver=lirc_imon
E: Ad=82(I) Atr=03(Int.) MxPS= 8 Ivl=10ms
```

What I highlighted in red I think is the problem. This identifies your device.  I looked at the lirc_imon.c file that I am 99% sure that you have.  This is the file that builds your driver. Your device is not supported!  
I went the latest code for your driver in the lirc at 
[http://lirc.cvs.sourceforge.net/viewvc/lirc/lirc/drivers/lirc_imon/lirc_imon.c?revision=1.33&view=markup](http://lirc.cvs.sourceforge.net/viewvc/lirc/lirc/drivers/lirc_imon/lirc_imon.c?revision=1.33&view=markup)
Your device is supported in that!!  Even though I have a different driver and device I had the same problem.  The lirc drivers in the repositories are ancient!  

1.Go to that link above and download that file
2.It would also be a good idea to get the lirc_dev.c driver(my lirc didn't work until I did that too).  That's at:
[http://lirc.cvs.sourceforge.net/viewvc/lirc/lirc/drivers/lirc_dev/lirc_dev.c?revision=1.62&view=markup](http://lirc.cvs.sourceforge.net/viewvc/lirc/lirc/drivers/lirc_dev/lirc_dev.c?revision=1.62&view=markup)
3. get lirc-modules-source from sudo apt-get install lirc-modules-source or synaptic
4. **If** your lirc-modules-source did not install into your home dir it probably went into /usr/src/lirc-*/ (* is wildcard for the version).  You will have to ```
cd /usr/src/lirc-*/lirc_imon
``` for the following steps
4. In the lirc-modules-source replace the older lirc_imon.c and lirc_dev.c with the new ones.
5. Rebuild and install your modules with dkms. Instructions are at this page: 
[https://help.ubuntu.com/community/InstallLirc/Hardy#Adding support for more remotes](https://help.ubuntu.com/community/InstallLirc/Hardy#Adding support for more remotes)
Go to step 6 there--pretty cool how the step numbers synced!  I did that without trying.  I think this should work for you.

---

### Post by Aphoxema on 2008-12-20
I'll go ahead and give that a shot, but I've been working off of the LIRC CVS before, I was hoping that was the bleeding edge I need.

---

### Post by Aphoxema on 2009-01-10
This didn't get me anywhere, I even booted off a livecd to do it to make sure I had a clean environment.

What information does anyone need to help me?

---

### Post by laceration on 2009-01-11
> I even booted off a livecd to do it
Is that the only way you tried it?

You booted into the live cd, installed lirc and followed the instructions and installed the modules?  I can't remember for sure but a reboot may have been necessary before it all worked.  Since you installed everything to ram, it would disappear after a reboot.

I don't think the live cd improved your chances of making it work.  If you follow the instructions in your normal environment, I think you have a good chance of it working.

---

