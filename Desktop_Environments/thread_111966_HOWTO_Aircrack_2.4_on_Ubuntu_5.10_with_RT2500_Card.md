---
title: "HOWTO: Aircrack 2.4 on Ubuntu 5.10 with RT2500 Card"
date: 2006-01-03
forum: Desktop Environments
---

### Post by akseli on 2006-01-03
Ok, so, for all of you trying to get aircrack 2.4 working in Ubuntu 5.10 (Breezy Badger) using a card based on the rt2500 chipset.

STEP 1: Perform a complete reinstall of Ubuntu **without** the rt2500 card inserted at any moment
STEP 2: Boot up into Ubuntu **without** your card inserted
STEP 3: Delete the pre-installed drivers for the rt2500 chipset:
```
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2500/
```
STEP 4: Download the current CVS-daily for the rt2500 drivers from [http://rtx00.serialmonkey.com](http://rtx00.serialmonkey.com)
STEP 5: Untar the downloaded file:
```
tar -xzf rt2500-cvs-daily.tar.gz
```
STEP 6: Build the driver module:
```
cd rt2500-cvs-*/Module
```
```
make
```
STEP 7: Copy the newly built module into your drivers folder:
```
sudo cp rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2500.ko
```
STEP 8: Now we make sure that everything is as it should be:
```
sudo ifdown ra0
```
If the output of this is "ra0 is not configured" or something of the sorts you are on your way to getting this working!
STEP 9: Actually configure the driver:
```
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500
```
```
sudo depmod
```

Now you have the correct drivers installed allowing you to use aireplay correctly, but to get everything to work you still need to complete phase two:

STEP 1: ```
 sudo modprobe rt2500
```
STEP 2: ```
sudo iwconfig ra0 mode monitor
```
STEP 3: ```
sudo iwpriv ra0 rfmontx 1
```
STEP 4: ```
sudo iwconfig ra0 channel x
```
STEP 5: ```
sudo ifconfig ra0 up
```

Now everything is setup and ready for using aircrack.
This is the easy part :) 

STEP 1: download aircrack-2.4.tgz
STEP 2: untar 
```
tar -xzf aircrack-2.4.tgz
```
STEP 3: build the programs
```
cd aircrack-2.4
```
```
make
```
STEP 4: install everything so you can run directly from a bash prompt
```
sudo make install
```

And there you go, you're done, everything should work and you can start probing your WLAN's security settings and trying to make your WLAN unpenetrable.

---please note that I cannot be held liable for any misuse of the software aforementioned---

---

### Post by sovin on 2006-02-24
```
sovin@sov-m-bb:~/Desktop/aircrack-2.41$ make
gcc -g -W -Wall -O2 -D_FILE_OFFSET_BITS=64 -D_MAJ=2 -D_MIN=41 linux/aircrack.c linux/crypto.c linux/sha1-mmx.S -o aircrack -lpthread
make: gcc: Command not found
make: *** [aircrack] Error 127
sovin@sov-m-bb:~/Desktop/aircrack-2.41$
```

I've been getting this after issuing the ```
make
``` command.  Any ideas what the problem is?

---

### Post by cbudden on 2006-02-24
[QUOTE=sovin]```
sovin@sov-m-bb:~/Desktop/aircrack-2.41$ make
gcc -g -W -Wall -O2 -D_FILE_OFFSET_BITS=64 -D_MAJ=2 -D_MIN=41 linux/aircrack.c linux/crypto.c linux/sha1-mmx.S -o aircrack -lpthread
make: gcc: Command not found
make: *** [aircrack] Error 127
sovin@sov-m-bb:~/Desktop/aircrack-2.41$
```

I've been getting this after issuing the ```
make
``` command.  Any ideas what the problem is?[/QUOTE]


sudo apt-get install build-essential

---

### Post by sovin on 2006-02-24
thank you,

Also, when I've been executing airodump eth1 testfile1 0 1, I recieve the following:

```
sovin@sov-m-bb:~/Desktop/aircrack-2.41$ sudo airodump eth1 testfile1 0 1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig eth1 up; iwconfig eth1 mode Monitor channel <#>'

```

I checked sudo ifconfig eth1 and sudo iwconfig eth1 and see no settings to change.  The link is _up_, and I had set my monitor channel earlier with airmon.sh

Could my Linksys wireless nic be at fault? (orinoco)...

---

### Post by KSDZ on 2006-03-02
Some way or another this causes to hang Dapper, when I insert my card...

too bad.

Any ideas on this?

---

### Post by onesojourner on 2006-10-07
I would also like to know how well this is playing with dapper.

---

