---
title: "Mediagate GP-IR02K MCE Remote Transmitter Problems"
date: 2009-03-02
forum: General Help
---

### Post by nerver on 2009-03-02
Hey everyone,

I have been beating my head against the wall for hours on this one and I am at my wits end. I'm hoping someone here is familiar with this remote and lirc to help me out.

I bought this remote because the mythtv wiki says it is well supported (and to be fair the reciever part works perfectly out of the box) but I just cannot get it to transmit anything. I tried using the infrared devices setup in Mytbuntu Control centre and set it to MCE V2 for the remote and transmitter sections and I have a lircd.conf, hardware.conf and the necessary conf files for the remote and the transmitting remote.

I have the same results after installing lirc 0.8.4a which has the correct hardware and manufacturer codes for this particular remote AFAIK.

Everything looks like it should be working when I test in terminal as all the modules are loaded and I get no error messages with irsend. I just can't get it to make the transmitter send anything and see no flashes on the emitter LED.

If anyone can I help I would greatly appreciate it.

Here is some relevant info:

```
sean@nerver:~$ ls -lAF /dev/lir*
crw-rw---- 1 root root 61, 0 2009-03-02 00:58 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-03-02 10:46 /dev/lircd=
srw-rw-rw- 1 root root     0 2009-03-02 10:46 /dev/lircd1=
```

```
sean@nerver:~$ lsmod | grep lirc
lirc_mceusb2           20228  1 
lirc_dev               20020  1 lirc_mceusb2
usbcore               149360  7 btusb,lirc_mceusb2,usb_storage,libusual,ohci_hcd,ehci_hcd
```

```
sean@nerver:~$ dmesg | grep -i lirc
[   25.012861] lirc_dev: IR Remote Control driver registered, major 61 
[   25.032525] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   25.032529] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   25.417171] lirc_dev: lirc_register_plugin: sample_rate: 0
[   25.421364] lirc_mceusb2[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:2
[   25.421921] usbcore: registered new interface driver lirc_mceusb2
```

irsend gives no error messages:
```

sean@nerver:~$ irsend SEND_ONCE SAE8000 2
sean@nerver:~$ 
```

Here is my hardware.conf:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lircd"
#TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
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

lircd.conf:

```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box transmitter:
include "/usr/share/lirc/transmitters/scientificatlanta/general.conf"
```

I can't think of anything else that is relevant but if more info is needed please let me know and I will post it asap.

Thank you,
-Sean

---

### Post by nerver on 2009-03-10
I ended up taking this remote back as I found a special at the same store that got me a PVR-150 MCE card and the standard black mce remote and transceiver for an extra $5 :) 

The remote that came with my pvr-150 works perfectly out of the box as does the ir transmitter so I guess the GP-IR02K transmitter is just not supported yet. Its too bad cause its a very nice looking remote that comes with it.

---

### Post by narfman0 on 2009-11-29
Hey all,

I got this remote working by filling out the buttons manually, as they are quite different codes than usual. Didn't put in numbers, radio/music/pictures, the mce button, colors, or clear/enter, but this'll get you working mostly. My lircd.conf, attached. (Put in /etc/lirc.)


```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Sun Nov 29 01:43:09 2009
#
# contributed by narfman0 
#
# brand: mediagate                      lircd.conf
# model no. of remote control: GP-IR02BK
# devices being controlled by this remote:
#

begin remote

  name  lircd.conf
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2686   870
  one           452   435
  zero          452   435
  pre_data_bits   24
  pre_data       0x1BFF83
  gap          106759
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          KEY_POWER                0x1BF3
          KEY_UP                   0x1BE1
          KEY_DOWN                 0x1BE0
          KEY_RIGHT                0x1BDE
          KEY_LEFT                 0x1BDF
          KEY_PAUSE                0x1BE7
          KEY_STOP                 0x1BE6
          KEY_ZOOM                 0x1BD8
          KEY_RECORD               0x1BE8
          KEY_REWIND               0x1BEA
          KEY_FORWARD              0x1BEB
          KEY_FASTFORWARD          0x1BE5
          KEY_ENTER                0x1BDD
          KEY_BACKSPACE            0x1BDC
          KEY_VOLUMEUP             0x1BEF
          KEY_VOLUMEDOWN           0x1BEE
          KEY_CHANNELUP            0x1BED
          KEY_CHANNELDOWN          0x1BEC
          KEY_MUTE                 0x1BF1
      end codes

end remote
```

---

### Post by narfman0 on 2009-12-03
Installing this on other computers revealed there's already a conf for this in /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb. It's there for fedora 12, ubuntu 9.4 and ubuntu 9.10. kbye (self pwn) Just cp to /etc/lirc/lircd.conf

---

### Post by doobiest on 2010-02-03
Can anyone help me to get this working?

I see the received listed in lsusb, but I do not see it under /proc/bus/input/devices.

I thought that was a requirement to get this working.

irw shows no captured buttons.

ubuntu 9.10

---

### Post by DLotus on 2010-06-18
Hello everyone,
I also recently bought a GP-IR02BK remote/blaster. The remote works great with 10.04 Mythbuntu 64bit, however I'm still having problems getting the blaster portion to work. I bought this to replace the blaster from the hauppauge HD-PVR due to the known problems everyone is having with the hauppauge blaster with it freezing / locking up the box.

I'll be happy to post any config files if needed, I have followed all the directions I could find, so I'm going to try a fresh install and start from the beginning since I wouldn't doubt that I hosed one of the config files with all the trial and error.

Thanks for the input

dlotus

---

### Post by PrvSAT on 2010-07-23
Hello folks,

I have the same Mediagate remote (GP-IR02BK) and I have the same problems, I can not make it work. From the reading above it does not show that anyone could make it work and I wonder why this thread has the tag as [SOLVED]???

---

### Post by nerver on 2010-07-23
hey PrvSAT,

I marked it solved cause it was my thread and I took the remote back and got a different one so the issue was "solved" for me. 

That being said, I did a lot of research on this before I took it back and as far as I'm aware the transmitter portion of this transceiver does not work with lirc. The receiver works beautifully but you wont be able to use the blaster. There may be someone out there that is willing/able to work on getting lirc to work with it, but because its an off-brand and fairly uncommon remote I'd say the odds of that happening are not good. 

You're best option is to take it back and try a different MCE remote tranciever and you will probably have it working right away. The other option if you really like the remote (because it is a really nice looking one) is to find/buy a different usb transceiver (that has a working blaster) and just use the mediagate remote with it.

I know its not a real solution but that's all I can recommend unfortunately.

Cheers,
-Sean

---

