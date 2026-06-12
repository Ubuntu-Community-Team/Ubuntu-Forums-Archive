---
title: "HOW TO: Install SCM SCR 243 PCMCIA smart card reader for DOD CAC cards"
date: 2008-12-09
forum: General Help
---

### Post by mmoses on 2008-12-09
[SIZE="4"]DOD CAC with a PCMCIA card reader on a laptop, Ubuntu 8.10 "Intrepid Ibex" with Linux 2.6.27-9-generic kernel.
[/SIZE]
Background:

I wanted to use a PCMCIA card reader as I had done with Windows.  I started here:

[http://ubuntuforums.org/showthread.php?t=564763&highlight=cac%20reader%20install]("http://ubuntuforums.org/showthread.php?t=564763&highlight=cac%20reader%20install")

Many, many thanks to psyopper and his sources for their work.  

I couldn't find any forum, site, or blog anywhere that talked about successfully doing this, so I started by trying to find a card supported by Linux drivers.  The two I had already, an ActivIdentity card and a SCM SCR201 were both non-starters.

There were two with drivers available - the Gemplus GPR-400 and the SCM SCR243.  I was off to Ebay where I picked up two SCR243's for $15 including shipping!  I then downloaded the drivers from the website: [http://www.scmmicro.com/support/pcs_product_drivers.html]("http://www.scmmicro.com/support/pcs_product_drivers.html")

Save the file and extract it to your home directory. Now we need to make a change to the includes file to update it for the new kernel.

:/$ cd ~/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src
 
:/$ sudo gedit includes.h 
		- remark out blockmem.h
		- change /asm/semaphore.h /linux/semaphore.h
....
#include <linux/semaphore.h> // this is the first change
#include <asm/io.h>
#include <asm/segment.h>
#include <asm/system.h>
#include <asm/unistd.h>
#include <asm/uaccess.h> // copy_to_user et al
#include <asm/delay.h>

//#include <pcmcia/version.h>

#include <pcmcia/cs_types.h>
#include <pcmcia/cs.h>
#include <pcmcia/cistpl.h>
#include <pcmcia/ciscode.h>
#include <pcmcia/ds.h>
#include <pcmcia/cisreg.h>
#include <pcmcia/ss.h>
//#include <pcmcia/bulkmem.h> // this is the second change
....

Some prep work with other required packages:

:/$ sudo apt-get install libusb-0.1-4 libpcsclite1 libpcsclite-dev pcscd pcsc-tools build-essential autoconf libccid

The original post also had the xlibs-dev package listed, but that has been deprecated, this works fine without it.

Now let's execute the install script:

:/$ cd ..
:/$ sudo ./install

The driver will not create the device file.  I don't know why but have a cheap workaround:

:/$ cd /dev
:/$ sudo mknod SCR24x0 c 251 0

To solve issue with device file not existing for driver load at startup, added to /lib/udev/devices as well...

:/$ cd /lib/udev/devices
:/$ sudo mknod SCR24x0 c 251 0

This would be a good time to seat your shiny new pcmcia card and restart the daemon:

:/$ sudo /etc/init.d/pcscd restart

What some commands should be showing if all is cooperating:

:/$ lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:06:09.0)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
Socket 0 Device 0:	[scr24x_cs]		(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   SCR243 PCMCIA Smart Card Reader 
	Identification:	manf_id: 0xffff	card_id: 0x0001
			prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
			prod_id(2): "Smart Card Reader" (0xf5a90d5d)
			prod_id(3): --- (---)
			prod_id(4): --- (---)
:/$ lsmod |grep pcmcia
pcmcia                 43052  1 SCR24x
pcmcia_core            43412  4 SCR24x,pcmcia,yenta_socket,rsrc_nonstatic

Insert your CAC card and running a pcsc_scan should return something like this:

:/$  pcsc_scan
PC/SC device scanner
V 1.4.14 (c) 2001-2008, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.99
Scanning present readers
0: SCR24x Smart Card Reader 00 00

Mon Dec  8 23:48:47 2008
 Reader 0: SCR24x Smart Card Reader 00 00
  Card state: Card inserted, Shared Mode, 
  ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1

ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
+ TS = 3B --> Direct Convention
+ T0 = DB, Y(1): 1101, K: 11 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU (223200 bits/s at 3.57 MHz)
  TC(1) = 00 --> Extra guard time: 0
  TD(1) = 80 --> Y(i+1) = 1000, Protocol T = 0 
-----
  TD(2) = 1F --> Y(i+1) = 0001, Protocol T = 15 - Global interface bytes following 
-----
  TA(3) = 03 --> Clock stop: not supported - Class accepted by the card: (3G) A 5V B 3V 
+ Historical bytes: 00 31 C0 64 77 E3 03 00 82 90 00
  Category indicator byte: 00 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: C0
        - Application selection: by full DF name
        - Application selection: by partial DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 4 (pre-issuing data)
      Data: 77 E3 03 00
    Mandatory status indicator (3 last bytes)
      LCS (life card cycle): 82 (Proprietary)
      SW: 9000 (Normal processing.)
+ TCK = C1 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
	CAC (Common Access Card)

Once you have success through these steps, the rest is easy:

:/$ sudo apt-get install coolkey

Next we need to set up Firefox to use your CAC/Reader as an authentication tool for websites. In Firefox go to:

Edit-> Preferences -> Advanced -> Encryption --
Click on the Security Devices button --
Click the Load button to load a new module. Name it CAC Module and type in /usr/lib/pkcs11/libcoolkeypk11.so
Press OK.

Now we install certificates - go here:
[http://dodpki.c3pki.chamb.disa.mil/rootca.html]("http://dodpki.c3pki.chamb.disa.mil/rootca.html")

Once there click on each of the three links, you will need to install all three certificates to get AKO/CAC working correctly. On each link, when you click it, Firefox will prompt you to install the certificate. Click Yes to each one.

That's it!  This updates the original post by psyopper, replacing the information for a USB reader with information for the SCM PCMCIA reader.  Now you can check your Navy email from Linux!

---

### Post by Bleumunkie on 2009-02-05
OUTSTANDING, Thank you for the walkthrough, it was EXACTLY what I needed.

One correction, 

```
:/$ sudo gedit includes.h 
- remark out blockmem.h
- change /asm/semaphore.h /linux/semaphore.h
....
#include <linux/semaphore.h> // this is the first change
#include <asm/io.h>
#include <asm/segment.h>
#include <asm/system.h>
#include <asm/unistd.h>
#include <asm/uaccess.h> // copy_to_user et al
#include <asm/delay.h>

//#include <pcmcia/version.h>

#include <pcmcia/cs_types.h>
#include <pcmcia/cs.h>
#include <pcmcia/cistpl.h>
#include <pcmcia/ciscode.h>
#include <pcmcia/ds.h>
#include <pcmcia/cisreg.h>
#include <pcmcia/ss.h>
//#include <pcmcia/bulkmem.h> // this is the second change
```

the first part should be "-remark out bulkmem.h" not "-remark out blockmem.h"

should look like this:

```
:/$ sudo gedit includes.h 
- remark out bulkmem.h
- change /asm/semaphore.h /linux/semaphore.h
....
#include <linux/semaphore.h> // this is the first change
#include <asm/io.h>
#include <asm/segment.h>
#include <asm/system.h>
#include <asm/unistd.h>
#include <asm/uaccess.h> // copy_to_user et al
#include <asm/delay.h>

//#include <pcmcia/version.h>

#include <pcmcia/cs_types.h>
#include <pcmcia/cs.h>
#include <pcmcia/cistpl.h>
#include <pcmcia/ciscode.h>
#include <pcmcia/ds.h>
#include <pcmcia/cisreg.h>
#include <pcmcia/ss.h>
//#include <pcmcia/bulkmem.h> // this is the second change
```


Potentially confusing since I tried using FIND to get to blockmem.h and it couldn't find it.

Otherwise GREAT walkthrough, works perfectly.

---

### Post by snaketopi on 2009-02-09
Hello there,

I've tried to use the great walkthrough to install my pcmcia card SCR243 but all what I get within the first step is a message as follows after the command sudo ./install (It seems there is a mistake with scr241_main.c):

snaketopi@snaketopi-laptop:~/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4$ sudo ./install
Kernel Headers located.
Kernel module has to be recompiled
Library is in /usr/lib
Installing ........
rm -f *.o
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~	
Compilng Release mode kernel module
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/scr241_main.o
/home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/scr241_main.c: In Funktion »Driver_Config«:
/home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/scr241_main.c:527: Warnung: Übergabe des Arguments 3 von »pccard_validate_cis« von inkompatiblem Zeigertyp
  CC [M]  /home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/PcdmHdlr.o
  CC [M]  /home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/PcdmRdWr.o
  CC [M]  /home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/ifd.o
  LD [M]  /home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/SCR24x.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/SCR24x.mod.o
  LD [M]  /home/snaketopi/Download/scr24x_v4.2.4_Release/scr24x_2.6.x_v4.2.4/src/SCR24x.ko
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.27-11-generic'
mkdir -p /lib/modules/`uname -r`/pcmcia
cp -f SCR24x.ko /lib/modules/`uname -r`/pcmcia/
depmod -A
rm -f *.o
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~	
rm -f *.o
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~	
Copied Release bundle
current reader.conf backedup as reader.conf.bak
Found pcsclite version 1.4.1
reader.conf updated
Pcmciautils present : copying UDEV scripts
                     :Done
Installation Complete.

I try to translate the German message as good as I can:

In function "Driver_Config" .../scr241_main.c:527: Warning: Completion of the argument 3 of 'pccard_validate_cis "from incompatible pointer type.

Hoping, everybody can help me.

---

### Post by tjc19999 on 2009-03-16
I'll have to admit, I purchased my product through Envoy Data here: [http://www.envoydata.com/security/scm/scr243.php]("http://www.envoydata.com/security/scm/scr243.php") and they support their products but they weren't as knowledgable as you linux gurus on this issue.

THANK YOU SO MUCH!!!  This saved me many hours of work.

---

### Post by lingenfr on 2009-04-18
I order to make the script run in Jaunty, I had to edit the install script so that it picked up the pcsc lite driver is folder /lib. Here is what I added:

------
#!/bin/bash
# Configure script for SCR241 Serial Smart Card Reader - 2.6 - Release
# Version 4.2.4 - Script works with both 'cardmgr' and 'pcmciautils'

currdir=`pwd`
COMPILE=0
act_kern=`uname -r`
exp_kern=2.6.20
module_path=/lib/modules/$act_kern/pcmcia
lib_path=/usr/local/scm/lib/
pcsc_version=`pcscd -v | grep version | cut -b19-23`
pcsc_120="1.2.0"

if test -d /lib/modules/$act_kern/build/include
then
	echo "Kernel Headers located."
else
	echo "Kernel headers to be installed. Install headers,"
	echo "and try again."
	exit
fi

if [ $act_kern != $exp_kern ]
then
    echo "Kernel module has to be recompiled"
    COMPILE=1
else
    COMPILE=0
fi

minor=`uname -r|cut -f2 -d.`

# Check if pcsclite daemon is installed
if [ -f /usr/lib/libpcsclite.so.1 ]; then
        pcsclib=/usr/lib
        echo "Library is in "$pcsclib
elif [ -f /usr/local/lib/libpcsclite.so.1 ]; then
        pcsclib=/usr/local/lib
        echo "Library is in "$pcsclib
#begin new section to make this work in Jaunty
elif [ -f /lib/libpcsclite.so.1 ]; then
        pcsclib=/lib
        echo "Library is in "$pcsclib
#end new section to make this work in Jaunty
elif [ -d /usr/pcsc/lib ]; then
        pcsclib=/usr/pcsc/lib
        echo "Library is in "$pcsclib
elif [ -d /usr/local/pcsc/lib ]; then
        pcsclib=/usr/local/pcsc/lib
        echo "Library is in "$pcsclib
else
        echo "pcsclite middleware is not installed."
        exit
fi

mkdir -p /usr/local/scm/lib &> /dev/null
mkdir -p /usr/local/scm/ini &> /dev/null
mkdir -p /lib/modules/$act_kern/pcmcia &> /dev/null

echo "Installing ........"	

# kernel module file installation
# if the current module version matches with the version
# for which the driver is compiled in, we dont do a re-compile.
if [ $COMPILE -eq 0 ]; then
	cp -f ./contrib/Release/*.ko /lib/modules/`uname -r`/pcmcia/
	depmod -A
	echo "Copied Release mode kernel module"
else
	cd ./src
	make clean
	echo "Compilng Release mode kernel module"
	make
	make install
	make clean
 	cd $currdir
fi

# Installation of the driver bundle.
cp -rf ./proprietary/Release/libSCR24x.so.4.2.1 /usr/local/scm/lib/
echo "Copied Release bundle"

ldconfig -n $lib_path

if test -f /etc/reader.conf
then
	 mv /etc/reader.conf /etc/reader.conf.bak
	 echo "current reader.conf backedup as reader.conf.bak"
fi

echo "Found pcsclite version $pcsc_version"

if [ $pcsc_version \> "1.2.8" ]; then
    cp ./contrib/reader.conf.1.2.9 /etc/reader.conf    
else
    cp ./contrib/reader.conf.$pcsc_version /etc/reader.conf    
fi

echo "reader.conf updated"

# Check whether the system has cardmgr or pcmciautils
# and proceed accordingly
cardctl &> /dev/null
CARDMGR=$?
pccardctl &> /dev/null
PCMCIAUTILS=$?

if [ $PCMCIAUTILS != 127 -a $CARDMGR == 127 ] 
then
	echo "Pcmciautils present : copying UDEV scripts"
	cp -f ./contrib/udev/80-scm-pcmcia.rules /etc/udev/rules.d
	cp -f ./contrib/udev/scr24x-node /etc/pcmcia
else
	echo "Copying cardmgr scripts"
	cp -f ./contrib/cardmgr/SCM.conf /etc/pcmcia
	cp -f ./contrib/cardmgr/smartcardreader-24x /etc/pcmcia
fi

echo "                     :Done"
echo "Installation Complete."
-----

I still can't get my SCR 241 to work. It worked under Intrepid following these instructions. Any assistance is appreciated.

---

### Post by sdible on 2009-04-27
I'm stumped...

I got this working just fine in 8.10, but I can't seem to get it to work at all in Jaunty...

Even following the steps above...

Are there any better Jaunty instructions anywhere?

---

### Post by sdible on 2009-04-28
Ok... here is my results from lspcmcia -v

```
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:04.0)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V
Socket 0 Device 0:	[-- no driver --]	(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   SCR243 PCMCIA Smart Card Reader 
	Identification:	manf_id: 0xffff	card_id: 0x0001
			prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
			prod_id(2): "Smart Card Reader" (0xf5a90d5d)
			prod_id(3): --- (---)
			prod_id(4): --- (---)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:04.1)
	Configuration:	state: on	ready: unknown
```

So, the card is definitely there...

Then I get the following...

```
lsmod |grep pcmcia
pcmcia                 44748  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
```

So something seems to be wrong.

As soon as I insert a card and do a pcsc_scan, it says there isn't a device.  I don't get it as I've done this a dozen times previously on 8.10.  What am I doing wrong?

Any suggestions?

---

### Post by Bleumunkie on 2009-05-06
> **sdible said:**
> Ok... here is my results from lspcmcia -v

```
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:04.0)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V
Socket 0 Device 0:	[-- no driver --]	(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   SCR243 PCMCIA Smart Card Reader 
	Identification:	manf_id: 0xffff	card_id: 0x0001
			prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
			prod_id(2): "Smart Card Reader" (0xf5a90d5d)
			prod_id(3): --- (---)
			prod_id(4): --- (---)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:04.1)
	Configuration:	state: on	ready: unknown
```

So, the card is definitely there...

Then I get the following...

```
lsmod |grep pcmcia
pcmcia                 44748  0 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
```

So something seems to be wrong.

As soon as I insert a card and do a pcsc_scan, it says there isn't a device.  I don't get it as I've done this a dozen times previously on 8.10.  What am I doing wrong?

Any suggestions?

First, your lspcmcia -v output is showing that there is no driver installed for the card.  where your output shows [--no driver--] it should show [scr24x_cs]. 

Here is my output from the same commands:

```
bleumunkie@bleumunkie-laptop:~$ lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:01:04.0)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
Socket 0 Device 0:	[scr24x_cs]		(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   SCR243 PCMCIA Smart Card Reader 
	Identification:	manf_id: 0xffff	card_id: 0x0001
			prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
			prod_id(2): "Smart Card Reader" (0xf5a90d5d)
			prod_id(3): --- (---)
			prod_id(4): --- (---)
bleumunkie@bleumunkie-laptop:~$ lsmod |grep pcmcia
pcmcia                 44748  1 SCR24x
pcmcia_core            43540  4 SCR24x,pcmcia,yenta_socket,rsrc_nonstatic

```

Second, I am almost certain the problem here lies in the /etc/reader.conf file.  if I use a USB reader (SCR331) it works fine.  Since the reader.conf file is not used for a USB reader - I think thats the weak point.

My reader.conf file looks like this - 

```
#Entry for SCR241 Serial Smart Card Reader

FRIENDLYNAME		"SCR24x Smart Card Reader"
DEVICENAME		/dev/SCR24x0
LIBPATH			/usr/local/scm/lib/libSCR24x.so
CHANNELID		0
```

I think the problem is the CHANNELID.  The documentation for the reader.conf file says this:

```
The "CHANNELID" is no more used for recent drivers (IFD handler 3.0) and
has been superseded by "DEVICENAME". If you have an old driver this
field is used to indicate the port to use. You should read your driver
documentation to know what information is needed here. It should be the
serial port number for a serial reader.
```

next step is to test it, however, this is where my skills are not up to par.

---

### Post by Flachzange on 2009-05-08
Hi together.

I had set up Ubuntu on my laptop last week for the first time, starting with 9.04. Then I noticed in the german forum that the SCR243 doesn't work on Jaunty and I stubbled across this thread. 

Today I had some time to follow the procedure for 8.10 and surprise surprise, it didn't work :-)

I read Bleumunkie's post and thought that it makes sense, so I started  to play with the CHANNELID value. According to the man page of reader.conf this value specifies the serial port number, so why not changing it to a number which does NOT exist.

First I tried -1 and it WORKED. I was surprised and tried all other numbers too and they also worked, even the default value. That was a bit weird and I did a reboot and everything was like before :/ So it couldn't be the CHANNELID, but what else have I done that made it work?

Yes... I plugged out the reader. So I plugged it out and in again, but nothing. Then I restarted the pcscd and suddenly it works again. This behavior is reproducible:

[B]1. Boot with plugged in pcmcia reader
2. Plug it out and in after startup
3. Restart pcscd deamon[/B]

But I cannot explain why it happens, but at least it works, even on Jaunty.

Christoph

---

### Post by Bleumunkie on 2009-05-10
I can confirm that what Flachzange works for me as well.  Next is how to fix it without the annoying work-around.  Thanks for the tip Flachzange!!

---

### Post by lingenfr on 2009-05-11
It doesn't work for me. I booted with the device inserted, popped it out and then reinserted, then I restarted pcscd and ran pcsc_scan. It still says waiting for the first reader. I tried changing the CHANNELID to 1 and going through the procedure again, still no joy. lspcmcia -v shows no driver loaded. Any other ideas?

---

### Post by sigkill__ on 2009-05-12
Just a heads up for people trying this guide with the HP Smartcard Reader (EL347AA) which is a SCR243. I banged my head trying to get this work, until i found instructions on [http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1242144482136+28353475&threadId=1185343](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1242144482136+28353475&threadId=1185343) how to solve this:

> you can use the original driver from SCM with a  simple modification.
Download the driver from SCM.
Extract the files, and find the file scr241_main.c
Search for the lines containing
PCMCIA_DEVICE_PROD_ID1("SCR243 PCMCIA",0x2054e8de),
PCMCIA_DEVICE_PROD_ID1("SCR24x PCMCIA",0x54a33665),
and add the line
PCMCIA_DEVICE_PROD_ID1("HP", 0x53cb94f9),

then use the script install to install the driver...everything should work now.

Background:
The driver from SCM detects the card by identifying the PROD_ID1 (see "pccardctl info"), but this strings has been changed by HP from "SCR243 PCMCIA" to simply "HP".....
So the driver from SCM just ignores this card, because this particular PROD_ID is not defined in the driver..Working fine on Jaunty for me, no need to edit includes.h with the newest drivers.
Thanks for this guide btw, really helped alot :)

---

### Post by kwr2k on 2009-09-02
Does this work with the USB smartcard reader as well? I have a SCM SCR301 usb reader and would be more than glad to get this working!

Thanks.

---

### Post by lingenfr on 2009-09-02
You don't need to go through all this for a usb cac reader. It is much simpler. Look on the community documentation website or just search your reader model. You just install a couple of apps from the repo, a little firefox tweaking and you are rocking. The PCMCIA readers however are still such a PITA as to be almost worthless.

---

### Post by tmfries on 2010-01-26
so I did the whole process and it I get a good output from lspcmcia -v:

Socket 0 Device 0:	[scr24x_cs]		(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   SCR243 PCMCIA Smart Card Reader 
	Identification:	manf_id: 0xffff	card_id: 0x0001
			prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
			prod_id(2): "Smart Card Reader" (0xf5a90d5d)
			prod_id(3): --- (---)
			prod_id(4): --- (---)

But my pcsc_scan comes back with no readers: 

PC/SC device scanner
V 1.4.15 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.102
Scanning present readers...
Waiting for the first reader...

I've tried reseating it and pscsd restart, but that doesn't seem to be working. Any ideas?

---

### Post by conor on 2010-03-09
> **tmfries said:**
> so I did the whole process and it I get a good output from lspcmcia -v:

But my pcsc_scan comes back with no readers: 

Had the same issue here. Moving the card reader from the bottom slot to the top slot works.

---

### Post by lingenfr on 2010-03-09
I no longer use my computer w/ PCMCIA hence I no longer use this device. However, I had some success using sudo /etc/init.d/pcscd restart when I had symptoms similar to yours. As stated above, I recommend that you either make contact with the pcsc developers or give up. I don't believe that anyone is looking at this and it is obviously broken worse than non-programmers can fix. I logically went through configuration files and tried different settings, etc but never got it to work reliably. I did get it to work, but it required so much futzing that I got sick of it and just used the USB reader which just worked. I'm unsubscribing from this thread. Good luck.

---

### Post by lubenthrust on 2010-05-10
Hi -- I registered just so I could comment on this post. For the first time in years I've been able to get my CAC to work in Ubuntu thanks to your help! Here are the steps I took to get things working:

First, I have an ActivCard PCMCIA, P/N: ZFG-9818-AA. It's basically a rebadged SCR 243. Second, I used the latest version of SCM's drivers, v4.2.6. I think they're dated April 19, 2009. Third, I performed the installation on Lucid 10.04 LTS, i386.

1.) Edit the install script. Follow lingenfr's instructions to add:

elif [ -f /lib/libpcsclite.so.1 ]; then
        pcsclib=/lib
        echo "Library is in "$pcsclib

at the appropriate location.

2.) Run the install script: sudo ./install

3.) Install the packages mmoses recommends: pcscd, etc.

4.) No need to mknod /dev/SCR24x0... the drivers work this time around. Or at least the driver is there after a reboot...

5.) I also did NOT mknod /lib/udev/devices/SCR24x0 -- may experiment with this later

6.) Running pcsc_scan after rebooting gives me the Waiting for first reader... hang. HOWEVER, restarting the pcsc daemon: sudo /etc/init.d/pcscd restart and then initiating pcsc_scan gets everything to work. No need to edit the channel number, remove/reinsert the reader, etc.

It's a bit of a hassle to restart the daemon whenever I want to use the card after a reboot, but oh well. At least it works. I'm afraid to do the mknod thing because I have no idea what it does.

---

### Post by tsimm on 2010-10-28
Hello,

SCR243 was working fine until I upgraded to 10.10.
Now I cannot compile drivers (compile log attached to post).

Do I need to install some packages or change some file?

Thanks

---

### Post by bachenke on 2011-02-07
I'm running Maverick and I just tried to make the SCR243 work with Ubuntu. After reading this thread and trying everything you've suggested I'm still at a dead end.

Here's my output after sudo ./install

```
Kernel Headers located.
Kernel module has to be recompiled
pcsclite middleware is not installed.
```Is that it? I was expecting more output than that.

lspcmcia -v gives me...

```
Socket 0 Device 0:    [-- no driver --]    (bus ID: 0.0)
    Configuration:    state: on
    Product Name:   SCR243 PCMCIA Smart Card Reader 
    Identification:    manf_id: 0xffff    card_id: 0x0001
            prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
            prod_id(2): "Smart Card Reader" (0xf5a90d5d)
            prod_id(3): --- (---)
            prod_id(4): --- (---)
```...indicating, quite clearly, no driver.

Has anybody been able to install the driver in Maverick? If so please paste your install-file content.

---

### Post by bachenke on 2011-02-08
> **lubenthrust said:**
> Hi -- I registered just so I could comment on this post. For the first time in years I've been able to get my CAC to work in Ubuntu thanks to your help! Here are the steps I took to get things working:

First, I have an ActivCard PCMCIA, P/N: ZFG-9818-AA. It's basically a rebadged SCR 243. Second, I used the latest version of SCM's drivers, v4.2.6. I think they're dated April 19, 2009. Third, I performed the installation on Lucid 10.04 LTS, i386.

1.) Edit the install script. Follow lingenfr's instructions to add:

elif [ -f /lib/libpcsclite.so.1 ]; then
        pcsclib=/lib
        echo "Library is in "$pcsclib

at the appropriate location.

2.) Run the install script: sudo ./install

3.) Install the packages mmoses recommends: pcscd, etc.

4.) No need to mknod /dev/SCR24x0... the drivers work this time around. Or at least the driver is there after a reboot...

5.) I also did NOT mknod /lib/udev/devices/SCR24x0 -- may experiment with this later

6.) Running pcsc_scan after rebooting gives me the Waiting for first reader... hang. HOWEVER, restarting the pcsc daemon: sudo /etc/init.d/pcscd restart and then initiating pcsc_scan gets everything to work. No need to edit the channel number, remove/reinsert the reader, etc.

It's a bit of a hassle to restart the daemon whenever I want to use the card after a reboot, but oh well. At least it works. I'm afraid to do the mknod thing because I have no idea what it does.

Reverted back to 10.04 and lubenthrust's guide worked :)

---

### Post by wgn on 2011-02-22
I have been able to get everything loaded (10.4 LTS).
The reader is ID'd properly, the driver is ID'd, and my CAC is recognized.

When I try to make the CAC Module in Firefox it tells me
"Unable to add module."

This is the same point I got to trying a USB SCR331.

Anybody know what I'm doing wrong?

---

### Post by wgn on 2011-02-22
Never mind.  I identified my screw up.
My SCR243 & CAC now work.

I didn't need to make the changes mmoses noted for the includes file.  The file has been revised to make those changes for kernels >= 2.6.27.
lingenfr's edit of the install script worked great.
I also did not have to create the device file, the driver loaded after a reboot.

Thanks for all the instructions.

---

### Post by mocambo on 2011-02-24
Anyway, officially available driver for SCM SCR243 works only for kernels <=2.6.29 . When tried to compile on 2.6.33, it gives following messages:

[INDENT][FONT="Courier New"]# ./install 
Kernel Headers located.
Kernel module has to be recompiled
Library is in /usr/lib
Installing ........
rm -f *.o
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~
Compilng Release mode kernel module
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-2.6.33.5-desktop586-2mnb'
  CC [M]  /home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.o
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_Attach’:
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:262: error: ‘irq_req_t’ has no member named ‘IRQInfo1’
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:265: error: ‘irq_req_t’ has no member named ‘IRQInfo2’
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:271: error: ‘irq_req_t’ has no member named ‘IRQInfo2’
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:275: warning: assignment from incompatible pointer type
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:276: error: ‘irq_req_t’ has no member named ‘Instance’
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘ConfigCheck’:
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:585: warning: passing argument 1 of ‘pcmcia_request_window’ from incompatible pointer type
include/pcmcia/ds.h:199: note: expected ‘struct pcmcia_device *’ but argument is of type ‘struct pcmcia_device **’
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_Config’:
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:712: error: implicit declaration of function ‘pcmcia_get_first_tuple’
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:713: error: implicit declaration of function ‘pcmcia_get_tuple_data’
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:751: error: ‘irq_req_t’ has no member named ‘IRQInfo1’
/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:753: error: ‘irq_req_t’ has no member named ‘IRQInfo2’
make[2]: *** [/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.o] Error 1
make[1]: *** [_module_/home/mocambo/Downloads/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.33.5-desktop586-2mnb'
make: *** [default] Error 2
mkdir -p /lib/modules/`uname -r`/pcmcia
cp -f SCR24x.ko /lib/modules/`uname -r`/pcmcia/
cp: cannot stat `SCR24x.ko': No such file or directory
make: *** [install] Error 1
rm -f *.o
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~
Copied Release bundle
current reader.conf backedup as reader.conf.bak
Found pcsclite version 1.5.5
reader.conf updated
Pcmciautils present : copying UDEV scripts
                     :Done
Installation Complete.
[/FONT][/INDENT]

If anybody have newer drivers or solutions, please let know.

---

### Post by wgn on 2011-02-24
I can't speak with regard to kernel 2.6.33, but it's working for me with 2.6.32-28.

---

### Post by wgn on 2011-02-24
> Library is in /usr/lib

Did you make lingenfr's edit to the install script [see post #5 of this thread]?  
The output should be echoing that the library is in /lib, not /usr/lib.

---

### Post by mocambo on 2011-02-24
> **wgn said:**
> Did you make lingenfr's edit to the install script [see post #5 of this thread]?  
The output should be echoing that the library is in /lib, not /usr/lib.

Thanks, but I've checked out - pcsc lite libraries are located in /usr/lib in my distribution.

The reason why original and lingenfr's scripts not work with 2.6.33, is caused by modificated kernel pcmcia driver sources.

These modifications appeared first on 2.6.33 and up, so Maverick wont work anymore with old drivers.

---

### Post by wgn on 2011-03-04
Does the driver need to be re-installed every time the kernel is updated?

It was working fine with 2.6.32-28, but after upgrading to 2.6.32-29 my reader didn't work anymore.
I ran lspcmcia -v and got the following output
```
william@william-laptop:~$ lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:03:01.0)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V
Socket 0 Device 0:	[-- no driver --]	(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   SCR243 PCMCIA Smart Card Reader 
	Identification:	manf_id: 0xffff	card_id: 0x0001
			prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
			prod_id(2): "Smart Card Reader" (0xf5a90d5d)
			prod_id(3): --- (---)
			prod_id(4): --- (---)

```
No driver.

I re-ran the install script, re-booted and now it's got a driver and everything works again.  Am I going to have to repeat this the next time the kernel updates?

---

### Post by blueice_haller on 2011-03-23
Hello,

I have installed a "two PCMCIA to one PCI adapter" with two SCR243 cardreaders.
One reader works fine and shows information at pcsc_scan.

But when I insert them both and eject one of them I get an kernel panic. But I need them both.

I hope this is helpful:
```
# lspcmcia -v
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.0)
        Configuration:  state: on       ready: yes
                        Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V
Socket 0 Device 0:      [-- no driver --]       (bus ID: 0.0)
        Configuration:  state: on
        Product Name:   SCR243 PCMCIA Smart Card Reader
        Identification: manf_id: 0xffff card_id: 0x0001
                        prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
                        prod_id(2): "Smart Card Reader" (0xf5a90d5d)
                        prod_id(3): --- (---)
                        prod_id(4): --- (---)
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.1)
        Configuration:  state: on       ready: yes
                        Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V
Socket 1 Device 0:      [-- no driver --]       (bus ID: 1.0)
        Configuration:  state: on
        Product Name:   SCR243 PCMCIA Smart Card Reader
        Identification: manf_id: 0xffff card_id: 0x0001
                        prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
                        prod_id(2): "Smart Card Reader" (0xf5a90d5d)
                        prod_id(3): --- (---)
                        prod_id(4): --- (---)
```
After installing the drivers and one inserted:
```
debian:~# lspcmcia -v
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.0)
        Configuration:  state: on       ready: yes
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.1)
        Configuration:  state: on       ready: yes
                        Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
Socket 1 Device 0:      [scr24x_cs]             (bus ID: 1.0)
        Configuration:  state: on
        Product Name:   SCR243 PCMCIA Smart Card Reader
        Identification: manf_id: 0xffff card_id: 0x0001
                        prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
                        prod_id(2): "Smart Card Reader" (0xf5a90d5d)
                        prod_id(3): --- (---)
                        prod_id(4): --- (---)
``````
# lspci
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
``````
# pcsc_scan
PC/SC device scanner
V 1.4.14 (c) 2001-2008, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.101
Scanning present readers
0: SCR24x Smart Card Reader 00 00

Wed Mar 23 17:14:04 2011
 Reader 0: SCR24x Smart Card Reader 00 00
  Card state: Card inserted,
  ATR: 3F FF 11 25 03 10 80 41 B0 07 69 FF 4A 50 70 00 00 50 31 01 00 11

ATR: 3F FF 11 25 03 10 80 41 B0 07 69 FF 4A 50 70 00 00 50 31 01 00 11
+ TS = 3F --> Inverse Convention
+ T0 = FF, Y(1): 1111, K: 15 (historical bytes)
  TA(1) = 11 --> Fi=372, Di=1, 372 cycles/ETU (9600 bits/s at 3.57 MHz)
  TB(1) = 25 --> Programming Param P: 5 Volts, I: 1 milliamperes
  TC(1) = 03 --> Extra guard time: 3
  TD(1) = 10 --> Y(i+1) = 0001, Protocol T = 0
-----
  TA(2) = 80 --> Protocol to be used in spec mode: T=0 - Unable to change - defined by interface bytes
+ Historical bytes: 41 B0 07 69 FF 4A 50 70 00 00 50 31 01 00 11
  Category indicator byte: 41 (proprietary format)

Possibly identified card (using /root/.smartcard_list.txt):
3F FF 11 25 03 10 80 41 B0 07 69 FF 4A 50 70 00 00 50 31 01 00 11
```

OS is debian 2.6.26-2-686. Used German article: [http://wiki.ubuntuusers.de/SCM_SCR_243_PCMCIA_SmartCard-Reader](http://wiki.ubuntuusers.de/SCM_SCR_243_PCMCIA_SmartCard-Reader)

---

### Post by wgn on 2011-03-23
I don't understand why you're ejecting one of them if you need them both.

When you lspcmcia -v with both inserted what do you get?  Do they both show up with drivers ID'd?

---

### Post by blueice_haller on 2011-03-23
Then I get the following:
```
# lspcmcia -v
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.0)
        Configuration:  state: on       ready: yes
                        Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
Socket 0 Device 0:      [scr24x_cs]             (bus ID: 0.0)
        Configuration:  state: on
        Product Name:   SCR243 PCMCIA Smart Card Reader
        Identification: manf_id: 0xffff card_id: 0x0001
                        prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
                        prod_id(2): "Smart Card Reader" (0xf5a90d5d)
                        prod_id(3): --- (---)
                        prod_id(4): --- (---)
Socket 1 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.1)
        Configuration:  state: on       ready: yes
                        Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
Socket 1 Device 0:      [scr24x_cs]             (bus ID: 1.0)
        Configuration:  state: on
        Product Name:   SCR243 PCMCIA Smart Card Reader
        Identification: manf_id: 0xffff card_id: 0x0001
                        prod_id(1): "SCR243 PCMCIA" (0x2054e8de)
                        prod_id(2): "Smart Card Reader" (0xf5a90d5d)
                        prod_id(3): --- (---)
                        prod_id(4): --- (---)
```
I don't know what the driver ID is.
pcsc_scan shows only one reader. Is it able to show two?

Perhaps, the problem is to create a second device-file on **/dev** and/or **/lib/udev/devices** ?
Or do I have to create a second in **/etc/reader.conf** ?

---

### Post by wgn on 2011-03-24
This says it's both readers with drivers correctly ID'd.
Post #29 said you ran pcsc_scan with one reader ejected.  What's the output when you run it with both readers installed?  I assume you've got two smart cards that you need read at the same time.  Even if you've only got one card right now it should show both readers, with one state as "Card removed".

---

### Post by blueice_haller on 2011-03-24
> **wgn said:**
> What's the output when you run it with both readers installed?The output is only about "Reader 0" - either information about the inserted Card or Card removed.
> **wgn said:**
> I assume you've got two smart cards that you need read at the same time.Exactly.
> **wgn said:**
> Even if you've only got one card right now it should show both readers, with one state as "Card removed".And this is exactly what pcsc_scan doesn't do.
If I use slot0, pcsc_scan shows info about "Reader 0".
If I use slot1 instead, pcsc_scan shows info about "Reader 0" - but it should show info about "Reader 1".

Perhaps any other software shows both readers. Note that I have installed non graphics mode.

---

### Post by wgn on 2011-03-25
I think you're on the right track with regard to **/etc/reader.conf**
Your **lspcmcia -v** output shows that there are two valid readers in the system, but **pscs_scan** says that the **pscsd** is only addressing one of them.

I don't have two SCR243's to experiment with, but I do have an SCR331 (somehwere) that I'll try to dig out this weekend and see if the problem is duplicated.  Granted, it's not exactly the same setup, but if **pscsd** is having problems with more than one reader at a time it should show up this way too.

I did find this [http://linux.die.net/man/8/update-reader.conf]("http://linux.die.net/man/8/update-reader.conf") which seems to be a way to force multiple readers into **/etc/reader.conf** but I haven't had a chance to figure out exactly how.  Google time.

---

### Post by wgn on 2011-04-01
Finally found the SCR331.  No joy.  I ran **pcsc_scan** alternately with my card in each reader.  
```
william@william-laptop:~$ pcsc_scan
PC/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.5.3
Scanning present readers...
0: SCR24x Smart Card Reader 00 00
1: SCM SCR 331 (21121010204885) 00 00

Fri Apr  1 12:52:34 2011
 Reader 0: SCR24x Smart Card Reader 00 00
  Card state: Card inserted, 
  ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1

ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
+ TS = 3B --> Direct Convention
+ T0 = DB, Y(1): 1101, K: 11 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU
    250000 bits/s at 4 MHz, fMax for Fi = 5 MHz => 312500 bits/s
  TC(1) = 00 --> Extra guard time: 0
  TD(1) = 80 --> Y(i+1) = 1000, Protocol T = 0 
-----
  TD(2) = 1F --> Y(i+1) = 0001, Protocol T = 15 - Global interface bytes following 
-----
  TA(3) = 03 --> Clock stop: not supported - Class accepted by the card: (3G) A 5V B 3V 
+ Historical bytes: 00 31 C0 64 77 E3 03 00 82 90 00
  Category indicator byte: 00 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: C0
        - Application selection: by full DF name
        - Application selection: by partial DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 4 (pre-issuing data)
      Data: 77 E3 03 00
    Mandatory status indicator (3 last bytes)
      LCS (life card cycle): 82 (Proprietary)
      SW: 9000 (Normal processing.)
+ TCK = C1 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
	CAC (Common Access Card)

Fri Apr  1 12:52:34 2011
 Reader 1: SCM SCR 331 (21121010204885) 00 00
  Card state: Card removed, 
^C
william@william-laptop:~$ pcsc_scan
PC/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.5.3
Scanning present readers...
0: SCR24x Smart Card Reader 00 00
1: SCM SCR 331 (21121010204885) 00 00

Fri Apr  1 12:53:05 2011
 Reader 0: SCR24x Smart Card Reader 00 00
  Card state: Card removed, 

Fri Apr  1 12:53:05 2011
 Reader 1: SCM SCR 331 (21121010204885) 00 00
  Card state: Card inserted, 
  ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1

ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
+ TS = 3B --> Direct Convention
+ T0 = DB, Y(1): 1101, K: 11 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU
    250000 bits/s at 4 MHz, fMax for Fi = 5 MHz => 312500 bits/s
  TC(1) = 00 --> Extra guard time: 0
  TD(1) = 80 --> Y(i+1) = 1000, Protocol T = 0 
-----
  TD(2) = 1F --> Y(i+1) = 0001, Protocol T = 15 - Global interface bytes following 
-----
  TA(3) = 03 --> Clock stop: not supported - Class accepted by the card: (3G) A 5V B 3V 
+ Historical bytes: 00 31 C0 64 77 E3 03 00 82 90 00
  Category indicator byte: 00 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: C0
        - Application selection: by full DF name
        - Application selection: by partial DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 4 (pre-issuing data)
      Data: 77 E3 03 00
    Mandatory status indicator (3 last bytes)
      LCS (life card cycle): 82 (Proprietary)
      SW: 9000 (Normal processing.)
+ TCK = C1 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
	CAC (Common Access Card)
^C

```
Both readers show up both times.  So **pcscd** is identifying both readers, but strangely **/etc/reader.conf** only shows the SCR243.
```

#Entry for SCR241 Serial Smart Card Reader

FRIENDLYNAME		"SCR24x Smart Card Reader"
DEVICENAME		/dev/SCR24x0
LIBPATH			/usr/local/scm/lib/libSCR24x.so
CHANNELID		0
```
I'm at a loss exactly where to go from here.

---

### Post by XruriniX on 2011-05-09
After putting a fresh build of Ubuntu 11.04 on my system, I tried getting my SRC-243 card reader installed.  I am still at the driver installation processes since several .h files were not available.

I followed every post in this thread and my problem is actually much worse now than when I started (but, of course, each post did point me towards the right direction, but none have addressed my current problem which seems to be an issue with the source code headers).  

Here is what I have done so far.  

[LIST=1]
[*]Downloaded the latest drivers
[*]Identified the correct directory for pcsc lib
[*]made necissary changes to install file
[*]identified missing cs.h and cs_types.h headers
[*]downloaded publically available versions the headers and placed them in the include/pcmcia directory
[/LIST]

Now, after trying to install the driver yet again I get an enormous list of errors (as opposed to only a few)

```
$ sudo ./install 
Kernel Headers located.
Kernel module has to be recompiled
Library is in /usr/lib/pcsc
Installing ........
rm -f *.o
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~	
Compilng Release mode kernel module
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.o
In file included from /home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/includes.h:106:0,
                 from /home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:52:
include/pcmcia/cistpl.h:18:23: error: redefinition of typedef ‘cisdata_t’
include/pcmcia/cs_types.h:26:19: note: previous declaration of ‘cisdata_t’ was here
In file included from /home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/includes.h:122:0,
                 from /home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:52:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/pcsc.h:268:2: error: expected specifier-qualifier-list before ‘dev_node_t’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:146:2: error: unknown field ‘ioctl’ specified in initializer
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:146:2: warning: initialization from incompatible pointer type
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_Attach’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:231:2: error: ‘DEVICE_EXTENSION’ has no member named ‘stWorkQueue’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:231:2: error: ‘DEVICE_EXTENSION’ has no member named ‘stWorkQueue’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:231:2: error: ‘DEVICE_EXTENSION’ has no member named ‘stWorkQueue’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:231:2: error: ‘DEVICE_EXTENSION’ has no member named ‘stWorkQueue’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:236:18: error: ‘DEVICE_EXTENSION’ has no member named ‘CardTracker’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:243:18: error: ‘DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:244:18: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:250:18: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsSystemResume’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:257:3: error: ‘DEVICE_EXTENSION’ has no member named ‘tqsEventWait’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:258:2: error: ‘DEVICE_EXTENSION’ has no member named ‘tqsReadEventWait’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:261:12: error: request for member ‘Attributes’ in something not a structure or union
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:261:26: error: ‘IRQ_TYPE_DYNAMIC_SHARING’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:261:26: note: each undeclared identifier is reported only once for each function it appears in
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:261:53: error: ‘IRQ_HANDLE_PRESENT’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:262:12: error: request for member ‘IRQInfo1’ in something not a structure or union
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:262:24: error: ‘IRQ_INFO2_VALID’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:262:42: error: ‘IRQ_LEVEL_ID’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:265:13: error: request for member ‘IRQInfo2’ in something not a structure or union
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:271:14: error: request for member ‘IRQInfo2’ in something not a structure or union
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:275:12: error: request for member ‘Handler’ in something not a structure or union
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:276:12: error: request for member ‘Instance’ in something not a structure or union
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:278:7: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:279:7: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:279:24: error: ‘INT_MEMORY_AND_IO’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_Detach’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:319:18: error: ‘DEVICE_EXTENSION’ has no member named ‘nStop’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:329:19: error: ‘DEVICE_EXTENSION’ has no member named ‘bSignalEvent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:330:19: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsEventSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:331:3: error: ‘DEVICE_EXTENSION’ has no member named ‘tqsReadEventWait’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:340:30: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:343:19: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:344:19: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsIrqSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:346:37: error: ‘DEVICE_EXTENSION’ has no member named ‘pDE_thread’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:347:19: error: ‘DEVICE_EXTENSION’ has no member named ‘pDE_thread’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_Suspend’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:403:18: error: ‘DEVICE_EXTENSION’ has no member named ‘nStop’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_Resume’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:442:30: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsIrqSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:442:69: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:445:3: error: ‘DEVICE_EXTENSION’ has no member named ‘tqsCardStatusWait’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:446:19: error: ‘DEVICE_EXTENSION’ has no member named ‘DE_thread_pid’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:456:37: error: ‘DEVICE_EXTENSION’ has no member named ‘byPcdmRev’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:461:20: error: ‘DEVICE_EXTENSION’ has no member named ‘byPcdmRev’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:466:21: error: ‘DEVICE_EXTENSION’ has no member named ‘byPcdmRev’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:474:21: error: ‘DEVICE_EXTENSION’ has no member named ‘byPcdmRev’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:483:19: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsSystemResume’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:487:18: error: ‘DEVICE_EXTENSION’ has no member named ‘nStop’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘ConfigCheck’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:495:2: error: ‘win_req_t’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:495:13: error: ‘req’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:495:30: error: expected expression before ‘)’ token
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:504:7: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:509:8: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:510:8: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:515:8: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:520:8: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:526:9: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:530:7: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:530:28: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:534:8: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:537:9: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:542:9: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:545:8: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:546:8: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:547:8: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:550:9: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:550:32: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:551:9: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:552:9: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:555:38: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:555:4: error: too many arguments to function ‘pcmcia_request_io’
include/pcmcia/ds.h:195:5: note: declared here
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:584:8: error: ‘struct pcmcia_device’ has no member named ‘win’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:585:43: error: ‘struct pcmcia_device’ has no member named ‘win’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:585:4: warning: passing argument 1 of ‘pcmcia_request_window’ from incompatible pointer type
include/pcmcia/ds.h:212:5: note: expected ‘struct pcmcia_device *’ but argument is of type ‘struct pcmcia_device **’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_Config’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:683:2: error: ‘win_req_t’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:683:13: error: expected ‘;’ before ‘req’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:684:2: warning: ISO C90 forbids mixed declarations and code
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:712:3: error: implicit declaration of function ‘pcmcia_get_first_tuple’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:713:3: error: implicit declaration of function ‘pcmcia_get_tuple_data’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:721:6: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:722:6: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:724:46: error: ‘req’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:724:2: warning: passing argument 2 of ‘pcmcia_loop_config’ from incompatible pointer type
include/pcmcia/ds.h:179:5: note: expected ‘int (*)(struct pcmcia_device *, void *)’ but argument is of type ‘int (*)(struct pcmcia_device *, struct cistpl_cftable_entry_t *, struct cistpl_cftable_entry_t *, unsigned int,  void *)’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:733:10: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:736:3: warning: passing argument 2 of ‘pcmcia_request_irq’ from incompatible pointer type
include/pcmcia/ds.h:207:18: note: expected ‘irq_handler_t’ but argument is of type ‘unsigned int *’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:741:20: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsIrqSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:742:20: error: ‘DEVICE_EXTENSION’ has no member named ‘bOrgIrqStatus’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:747:20: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsIrqSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:748:20: error: ‘DEVICE_EXTENSION’ has no member named ‘bOrgIrqStatus’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:751:16: error: request for member ‘IRQInfo1’ in something not a structure or union
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:751:28: error: ‘IRQ_INFO2_VALID’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:753:17: error: request for member ‘IRQInfo2’ in something not a structure or union
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:753:29: error: ‘IRQ_HANDLE_PRESENT’ undeclared (first use in this function)
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:766:2: error: implicit declaration of function ‘pcmcia_request_configuration’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:766:2: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:773:11: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:775:4: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:775:4: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:777:11: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:779:4: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:779:4: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:785:26: error: ‘DEVICE_EXTENSION’ has no member named ‘DeviceNode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:786:18: error: ‘DEVICE_EXTENSION’ has no member named ‘DeviceNode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:787:18: error: ‘DEVICE_EXTENSION’ has no member named ‘DeviceNode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:792:33: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:795:6: error: ‘struct pcmcia_device’ has no member named ‘dev_node’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:795:36: error: ‘DEVICE_EXTENSION’ has no member named ‘DeviceNode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:800:10: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:804:9: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:805:9: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:808:10: error: ‘struct pcmcia_device’ has no member named ‘conf’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:813:10: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:815:38: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:816:7: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:816:26: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:818:10: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:820:36: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:821:7: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:821:26: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:823:10: error: ‘struct pcmcia_device’ has no member named ‘win’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:833:41: error: ‘struct pcmcia_device’ has no member named ‘io’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:835:18: error: ‘DEVICE_EXTENSION’ has no member named ‘bSignalEvent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:839:18: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsQueueSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:847:31: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsIrqSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:849:3: error: ‘DEVICE_EXTENSION’ has no member named ‘tqsCardStatusWait’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:850:19: error: ‘DEVICE_EXTENSION’ has no member named ‘DE_thread_pid’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:852:19: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_InitLocal’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2059:19: error: ‘DEVICE_EXTENSION’ has no member named ‘prevCardStatus’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2060:19: error: ‘DEVICE_EXTENSION’ has no member named ‘cardStsChange’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2065:19: error: ‘DEVICE_EXTENSION’ has no member named ‘byPcdmRev’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2077:20: error: ‘DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘IFDHClose’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2166:31: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2168:87: error: ‘DEVICE_EXTENSION’ has no member named ‘bOrgIrqStatus’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2170:20: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2171:20: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsIrqSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2171:50: error: ‘DEVICE_EXTENSION’ has no member named ‘bOrgIrqStatus’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2173:32: error: ‘DEVICE_EXTENSION’ has no member named ‘bOrgIrqStatus’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2177:39: error: ‘DEVICE_EXTENSION’ has no member named ‘pDE_thread’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘IFDHIoctl’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2225:23: error: ‘DEVICE_EXTENSION’ has no member named ‘nStop’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2272:48: error: ‘DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2286:20: error: ‘DEVICE_EXTENSION’ has no member named ‘pucFwBuffer’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2289:33: error: ‘DEVICE_EXTENSION’ has no member named ‘pucFwBuffer’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2294:4: error: ‘DEVICE_EXTENSION’ has no member named ‘pucFwBuffer’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2295:20: error: ‘DEVICE_EXTENSION’ has no member named ‘ulOffset’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2302:31: error: ‘DEVICE_EXTENSION’ has no member named ‘ulOffset’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2304:30: error: ‘DEVICE_EXTENSION’ has no member named ‘pucFwBuffer’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2309:4: error: ‘DEVICE_EXTENSION’ has no member named ‘pucFwBuffer’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2314:20: error: ‘DEVICE_EXTENSION’ has no member named ‘ulOffset’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2320:74: error: ‘DEVICE_EXTENSION’ has no member named ‘pucFwBuffer’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2337:32: error: ‘DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2346:32: error: ‘DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2379:33: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2381:22: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2382:6: error: ‘DEVICE_EXTENSION’ has no member named ‘tqsCardStatusWait’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2383:22: error: ‘DEVICE_EXTENSION’ has no member named ‘DE_thread_pid’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2389:33: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2392:22: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2393:22: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsIrqSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2393:52: error: ‘DEVICE_EXTENSION’ has no member named ‘bOrgIrqStatus’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2394:40: error: ‘DEVICE_EXTENSION’ has no member named ‘pDE_thread’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2395:22: error: ‘DEVICE_EXTENSION’ has no member named ‘pDE_thread’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2401:48: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsIrqSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2407:20: error: ‘DEVICE_EXTENSION’ has no member named ‘byPcdmRev’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘IFDHRead’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2470:24: error: ‘DEVICE_EXTENSION’ has no member named ‘nStop’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2478:31: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsSystemResume’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2481:20: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsSystemResume’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘Driver_IrqHandler’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2631:23: error: ‘DEVICE_EXTENSION’ has no member named ‘nStop’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2638:30: error: ‘DEVICE_EXTENSION’ has no member named ‘bIsPolledMode’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘tqGetCardStatus’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2672:21: error: ‘DEVICE_EXTENSION’ has no member named ‘stWorkQueue’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2672:21: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2672:21: warning: initialization from incompatible pointer type
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2672:21: error: ‘DEVICE_EXTENSION’ has no member named ‘stWorkQueue’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2677:23: error: ‘struct _DEVICE_EXTENSION’ has no member named ‘nStop’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2682:31: error: ‘struct _DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2687:18: error: ‘struct _DEVICE_EXTENSION’ has no member named ‘bIsQueueSet’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c: In function ‘PcdmCardStatusThread’:
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2704:30: error: ‘struct _DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2722:51: error: ‘struct _DEVICE_EXTENSION’ has no member named ‘tqsCardStatusWait’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2737:32: error: ‘struct _DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.c:2746:34: error: ‘struct _DEVICE_EXTENSION’ has no member named ‘bBootRomPresent’
make[2]: *** [/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src/scr241_main.o] Error 1
make[1]: *** [_module_/home/mike/Downloads/SRC243/scr24x_v4.2.6_Release/scr24x_2.6.x_v4.2.6/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [default] Error 2
mkdir -p /lib/modules/`uname -r`/pcmcia
cp -f SCR24x.ko /lib/modules/`uname -r`/pcmcia/
cp: cannot stat `SCR24x.ko': No such file or directory
make: *** [install] Error 1
rm -f *.o
rm -f *.ko
rm -f *.mod.*
rm -f .*.cmd
rm -rf .tmp_*
rm -f *~	
Copied Release bundle
current reader.conf backedup as reader.conf.bak
Found pcsclite version 1.7.0
reader.conf updated
Pcmciautils present : copying UDEV scripts
                     :Done
Installation Complete.

```

When all is said and done, I still don't have a driver.  Anyone ever try this on 11.04?  I was pretty upset to see that this brand is the only one which drivers are not already included in the repository.

---

### Post by Magliter on 2012-01-13
Any updates on this issue? I'm coming across the same problems....

---

### Post by wgn on 2012-01-13
I got one of the new CAC cards in June and haven't been able to get it to work since then.  Finally gave up trying to make it work in Ubuntu.  Started using LPS.

[http://www.spi.dod.mil/lipose.htm]("http://www.spi.dod.mil/lipose.htm")

It works without having to play around.  Not a perfect solution, but good enough.

---

### Post by xuri on 2012-01-27
i have ubuntu 11.10 and i have the same problem

The Pcmcia card is scr24X, but is named "HP".

Socket 0 Device 0:      [-- no driver --]       (bus ID: 0.0)
        Configuration:  state: on
        Product Name:   HP PC Card Smart Card Reader 
        Identification: manf_id: 0xffff card_id: 0x0001
                        prod_id(1): "HP" (0x53cb94f9)
                        prod_id(2): "PC Card Smart Card Reader" (0xbfdf89a5)
                        prod_id(3): --- (---)
                        prod_id(4): --- (---)


i can't compile it to kernel 3.0.0.15-pae.

Somebody can help me?

when i tried to compile, it has errors ( cs_types.h not found, cs.h not found.. etc )

---

### Post by xuri on 2012-02-02
if you're interested with a new driver for kernels starting 3.0, please contact with scmmicro.com.

I contact with them, and say me:

 --------------

we unfortunately do not have a driver for the Linux kernels starting with 2.6.36.

 

Development will have to adapt the driver fir the older kernels to the new circumstances find with the newer kernels.

Due to the very low demand for adapted drivers, this is a low priority task (you’re the only one asking for a driver to support kernel 3.x), so I cannot really say, when an adapted driver will become available. Sorry for that.

 

Mit freundlichen Grüßen / Best Regards

Uwe Arends
-----------------

if more people is interested with this driver, is probably that her priority is high.

Sorry, but my english is really bad.

---

### Post by optimisteo on 2012-06-27
Hi,

Same problem here. I recently contacted them for a recent kernel linux driver. Havent got a reply yet but it will most probably be the same you received.

I'll keep u updated on that.

Anyone needing a recent linux driver please let them know as well it might leverage our persuasion powers ;)



SUPPORT FORM:

identive-infrastructure.com/crequest.php?page=4

Cheers,

Opti.

---

