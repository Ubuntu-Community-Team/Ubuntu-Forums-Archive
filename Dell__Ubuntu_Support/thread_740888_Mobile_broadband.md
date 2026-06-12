---
title: "Mobile broadband"
date: 2008-03-31
forum: Dell  Ubuntu Support
---

### Post by Martin Nilsson on 2008-03-31
I have a Dell Wireless 5520 Generic Mobile Broadband 3G HSDPA, Expedite EU870D Minicard  build in my XPS M1330.

Now I would like to use Ubuntu as operating system and I can't find a driver for the Mobile Broadband to install?

/Martin

---

### Post by mick8985 on 2008-03-31
Can you give the output of lspci?

---

### Post by barichardson5727 on 2008-04-02
lspci wont give the output needs to make this work. 
lsusb will be the command to use to determine the vendor/device ids.

I have the 5720 card in my laptop and you can use this method to get yours working, all you should have to change is the vendor and device ids to match the output of lsusb. 

Here is an example of my configuration:
```
root@rasengan:~# lsusb
Bus 005 Device 002: ID 046d:08c6 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:8134 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

What I can gather from this output is that my vendor id=0x413c and my product id=0x8134.

so now I will load the usbserial module on this device:
```
root@rasengan:~# modprobe usbserial vendor=0x413c product=0x8134
```

Now that the module is loaded you will need to create your confiuration files for pppd. There will be two files that we will need to create.

You will create a file in /etc/ppp/peers/wwan. Here is an output of my configuration:
```
root@rasengan:~# cat /etc/ppp/peers/wwan 
-detach
ttyUSB0
115200
debug
noauth
defaultroute
usepeerdns
user $XXXXXXXXXX@sprintpcs.com
show-password
crtscts
lock
lcp-echo-failure 4
lcp-echo-interval 65535
connect '/usr/sbin/chat -v -t3 -f /etc/chatscripts/wwan
```
note: I replaced my phone number with "XXX", you should modify this to match your phone number assigned to your account. I actually don't think this entry is needed at all, but I have included it anyway.

The next file you will create is /etc/chatscripts/wwan:
```
root@rasengan:~# cat /etc/chatscripts/wwan
'' 'AT'
'OK' 'ATZ'
'OK' 'ATE0V1&F&D2&C1&C2S0=0'
'OK' 'ATE0V1'
'OK' 'ATS7=60'
'OK' 'ATDT#777'
CONNECT CLIENT
```

In order to use the interface you can just use the following command:
```
root@rasengan:~# pppd call wwan
```

You should connect and be able to use the internet in your wireless broadband adapter if everything goes as planned. Keep in mind that the configuration I was providing for examples was for sprint EVDO, so there could be some minor changes for cingular HSDPA but I am sure that will get you started. I do not have any cingular devices to test with but just let us know if you run into any problems with your configuration and post your findings here.

I also assume you could just install a pppd gui interface such as kpppd to avoid working with the config files, but you will just have to experiment with the various methods to see what you like best. 

Also, since your adapter is integrated you may want have it load the modules at boot, I don't allow mine to load at boot since I normally use wlan when I an within range and only activate my wwan when I need it.

---

### Post by anaspeople on 2008-04-02
I get this error when I try all steps above

```
root@txo:~# pppd call wwan
pppd: In file /etc/ppp/peers/wwan: unrecognized option 'ttyUSB0'

```

Any idea?

---

### Post by timcredible on 2008-04-02
you probably just need to run gnome-ppp, no drivers needed if it's showing up as usb.  check out how to run the verizon usb-connected cards [here,]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=19&Itemid=27") maybe it will help with your card.  note:  gnome-ppp in 7.10 has a bug where it never shows it's connected, you can run kppp instead or just ignore the fact that gnome-ppp never says 'connected'.

---

### Post by barichardson5727 on 2008-04-02
Its possible that your card may not be located at /dev/ttyUSB0. You could try the changing the option to ttyUSB1 in your peers file and see if that works. 

Also, run this command to see if you even have those devices available:
```
root@rasengan:~# ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1
```

If you dont have the ttyUSB devices most likely the usbserial module was not loaded correctly, so you will want to verify that you are using the correct vendor/device ids to match your card.

---

### Post by barichardson5727 on 2008-04-02
I do  agree that kppp will probably make this much easier, and its easy to use.

---

### Post by anaspeople on 2008-04-02
My lsusb output is:
```
root@txo:~# lsusb
Bus 007 Device 004: ID 05ac:1203 Apple Computer, Inc. 
Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 005: ID 413c:8126 Dell Computer Corp. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

So I did:
```
modprobe usbserial vendor=0x413c product=0x8126
```
So now I do have a device at /dev/ttyUSB0

I've used gnome-ppp, but with the following error (modem not responding):
```
/home/nko/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!"
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.

```

I have configured it using info from [http://www.ubuntu-es.org/index.php?q=node/33041]("http://www.ubuntu-es.org/index.php?q=node/33041")
to use it with vodafone spain.

Anyway I think the problem is before even using this configuration...

---

### Post by anaspeople on 2008-04-02
I think I found the reason myself.
I've checked the BIOS and found out this:
> Cellular Device = {none} 
So I guess eventhough I have a small slot with a SIM card image on it, there's really no hardware there. What a crap!
Sorry for the expression but I feel very disappointed right now.

Lucky you ;)

---

### Post by nowhere@cox.net on 2008-04-02
Just an FYI for anyone reading this thread. You can use the airprime driver instead of usbserial to possibly more than triple your download speeds. I am using a Novatel U727 USB card and previously I was using the very popular usbserial fix to connect at 500-600kbps.  I have since recompiled the airprime driver and my speeds tripled. There is one line in the driver source you need to add with the vendor and product code of your device. Then you can recompile just the airprime driver and copy it over the standard Gutsy one. 

In my case, the U727 has a microSD slot as well so I have to load the usbserial module with the vendor and product code, then load my new airprime driver then I am good to go at 2100kbps. 

[[IMG]http://www.speedtest.net/result/254397676.png[/IMG]](http://www.speedtest.net) 

If there is interest and I can find time I can make a HOWTO...

Cheers,
Eric

---

### Post by barichardson5727 on 2008-04-02
I have actually been planning on going to the airprime module as well but have not yet had a chance to actually give it a try. I may try this tonight and will probably post some quick instructions for anyone interested but it shouldn't be difficult at all as like you said you just have to add your device/vendor ids module.

---

### Post by barichardson5727 on 2008-04-02
ok...so I have mine working now with the airprime modules. I noticed a huge difference immediately. Here is a link to some pretty good step by step instructions for using the airprime modules:
[http://ubuntuforums.org/archive/index.php/t-461991.html](http://ubuntuforums.org/archive/index.php/t-461991.html)

---

### Post by christoffv on 2008-04-07
Hi guys

Thanks for this thread, but I still have problems to use my onboard "Expedite EU870D MiniCard" in my Dell Latitude D830

I have followed all the howto's to the point I would appriciate it if any body can please kick me in the right direction.

Thanks Christoff

Included is all my config files, i am really desperate.

lsusb
Bus 002 Device 004: ID 413c:8137 Dell Computer Corp.

/etc/modules
usbserial vendor=0x413c product=0x8137

Minicom output:
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
OK
ati3
Manufacturer: Novatel Wireless Incorporated
Model: Expedite EU870D MiniCard
Revision: 10.9.0102.0-00  [2007-07-03 13:50:21]
IMEI: 355380013057507
+GCAP: +CGSM,+DS

/etc/ppp/peers/wwvan
-detach
ttyUSB0
115200
debug
noauth
defaultroute
usepeerdns
user web
show-password
crtscts
lock
lcp-echo-failure 4
lcp-echo-interval 65535
connect '/usr/sbin/chat -v -t3 -f /etc/chatscripts/wwan

/etc/chatscripts/wwvan
'' 'AT'
'OK' 'ATZ'
'OK' 'ATE0V1&F&D2&C1&C2S0=0'
'OK' 'ATE0V1'
'OK' 'ATS7=60'
'OK' 'ATDT*99***1#'
CONNECT


I also used comgt utility, The output from 
comgt info -d /dev/ttyUSB0
##### Wireless WAN Modem Configuration #####
Product text:
====

Manufacturer: Novatel Wireless Incorporated
Model: Expedite EU870D MiniCard
Revision: 10.9.0102.0-00  [2007-07-03 13:50:21]
IMEI: 355380013057507
+GCAP: +CGSM,+DS
OK
====
Manufacturer:           Novatel Wireless Incorporated
IMEI and Serial Number: 355380013057507
Manufacturer's Revision:
10.9.0102.0-00  [2007-07-03 13:50:2
Hardware Revision:

Network Locked:         0
Customisation:

Band settings:          (
)
APN:                    1,"IP","internet","",0,0
##### END #####

sig -d /dev/ttyUSB0
Signal Quality: 99,99

comgt reg -d /dev/ttyUSB0
Waiting for Registration.............................................................
Failed to register

May here I am missing something due to the fact that is does not register.


If I run pppd call wwvan

i get the following output:
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]

---

### Post by barichardson5727 on 2008-04-07
I did see one thing that sticks out in your config files, if you look at the last line of your /etc/ppp/peers/wwvan it is referecing a file in /etc/chatscripts that does not exist. 

change the last line in /etc/ppp/peers/wwvan to the following and try again:
```
connect '/usr/sbin/chat -v -t3 -f /etc/chatscripts/wwvan'
```

---

### Post by christoffv on 2008-04-08
Thanks for the reply, i have check all the file names and all was happy, but now I get the following output.

Apr  8 06:49:29 f3339041 pppd[6815]: PAP authentication succeeded
Apr  8 06:49:29 f3339041 pppd[6815]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Apr  8 06:49:29 f3339041 pppd[6815]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Apr  8 06:49:29 f3339041 pppd[6815]: rcvd [LCP ProtRej id=0x3 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Apr  8 06:49:29 f3339041 pppd[6815]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Apr  8 06:49:32 f3339041 pppd[6815]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Apr  8 06:49:59 f3339041 pppd[6815]: IPCP: timeout sending Config-Requests
Apr  8 06:49:59 f3339041 pppd[6815]: sent [LCP TermReq id=0x2 "No network protocols running"]
Apr  8 06:50:02 f3339041 pppd[6815]: sent [LCP TermReq id=0x3 "No network protocols running"]
Apr  8 06:50:05 f3339041 pppd[6815]: Connection terminated.
Apr  8 06:50:06 f3339041 pppd[6815]: Modem hangup

I am currently trying to google for this error, Apr  8 06:49:29 f3339041 pppd[6815]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received, but no luck so far.

Cheers
Christoff
Apr  8 06:50:06 f3339041 pppd[6815]: Exit.

---

### Post by barichardson5727 on 2008-04-08
I figured this may be helpful, here is the output that I get upon a successful connection. You can compare this tor your output. I dont think that "pppd[6815]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received" is where your problem is, as I get the same output on a successful connection.
Have you tried to make a connection from Windows? I know that you have to initially activate the card in windows before it can be used in Linux.

```

root@rasengan:~# pppd call wwan
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xae4857ff> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <magic 0x9cccfa90> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <magic 0x9cccfa90> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xae4857ff> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xae4857ff]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP DiscReq id=0x1 magic=0x9cccfa90]
rcvd [LCP EchoRep id=0x0 magic=0x9cccfa90 ae 48 57 ff]
rcvd [IPCP ConfReq id=0x0 <addr 68.28.185.69>]
sent [IPCP ConfAck id=0x0 <addr 68.28.185.69>]
rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 70.3.25.90> <ms-dns1 68.28.186.91> <ms-dns3 68.28.178.91>]
sent [IPCP ConfReq id=0x3 <addr 70.3.25.90> <ms-dns1 68.28.186.91> <ms-dns3 68.28.178.91>]
rcvd [IPCP ConfAck id=0x3 <addr 70.3.25.90> <ms-dns1 68.28.186.91> <ms-dns3 68.28.178.91>]
not replacing existing default route via 192.168.1.1
Cannot determine ethernet address for proxy ARP
local  IP address 70.3.25.90
remote IP address 68.28.185.69
primary   DNS address 68.28.186.91
secondary DNS address 68.28.178.91
Script /etc/ppp/ip-up started (pid 18502)
Script /etc/ppp/ip-up finished (pid 18502), status = 0x0

```


Also, here is the output that to /var/log/messages when I start a connection:

```
Apr  8 03:02:14 rasengan pppd[18464]: pppd 2.4.4 started by brad, uid 0
Apr  8 03:02:15 rasengan chat[18476]: send (AT^M)
Apr  8 03:02:15 rasengan chat[18476]: expect (OK)
Apr  8 03:02:15 rasengan chat[18476]: AT^M^M
Apr  8 03:02:15 rasengan chat[18476]: OK
Apr  8 03:02:15 rasengan chat[18476]:  -- got it 
Apr  8 03:02:15 rasengan chat[18476]: send (ATZ^M)
Apr  8 03:02:15 rasengan chat[18476]: expect (OK)
Apr  8 03:02:15 rasengan chat[18476]: ^M
Apr  8 03:02:16 rasengan chat[18476]: ATZ^M^M
Apr  8 03:02:16 rasengan chat[18476]: OK
Apr  8 03:02:16 rasengan chat[18476]:  -- got it 
Apr  8 03:02:16 rasengan chat[18476]: send (ATE0V1&F&D2&C1&C2S0=0^M)
Apr  8 03:02:16 rasengan chat[18476]: expect (OK)
Apr  8 03:02:16 rasengan chat[18476]: ^M
Apr  8 03:02:16 rasengan chat[18476]: ATE0V1&F&D2&C1&C2S0=0^M^M
Apr  8 03:02:16 rasengan chat[18476]: OK
Apr  8 03:02:16 rasengan chat[18476]:  -- got it 
Apr  8 03:02:16 rasengan chat[18476]: send (ATE0V1^M)
Apr  8 03:02:16 rasengan chat[18476]: expect (OK)
Apr  8 03:02:16 rasengan chat[18476]: ^M
Apr  8 03:02:16 rasengan chat[18476]: ATE0V1^M^M
Apr  8 03:02:16 rasengan chat[18476]: OK
Apr  8 03:02:16 rasengan chat[18476]:  -- got it 
Apr  8 03:02:16 rasengan chat[18476]: send (ATS7=60^M)
Apr  8 03:02:16 rasengan chat[18476]: expect (OK)
Apr  8 03:02:16 rasengan chat[18476]: ^M
Apr  8 03:02:16 rasengan chat[18476]: ^M
Apr  8 03:02:16 rasengan chat[18476]: OK
Apr  8 03:02:16 rasengan chat[18476]:  -- got it 
Apr  8 03:02:16 rasengan chat[18476]: send (ATDT#777^M)
Apr  8 03:02:16 rasengan chat[18476]: expect (CONNECT)
Apr  8 03:02:16 rasengan chat[18476]: ^M
Apr  8 03:02:17 rasengan chat[18476]: ^M
Apr  8 03:02:17 rasengan chat[18476]: CONNECT
Apr  8 03:02:17 rasengan chat[18476]:  -- got it 
Apr  8 03:02:17 rasengan chat[18476]: send (CLIENT^M)
Apr  8 03:02:17 rasengan pppd[18464]: Serial connection established.
Apr  8 03:02:17 rasengan pppd[18464]: Using interface ppp0
Apr  8 03:02:17 rasengan pppd[18464]: Connect: ppp0 <--> /dev/ttyUSB0
Apr  8 03:02:19 rasengan kernel: [15455.795108] PPP BSD Compression module registered
Apr  8 03:02:19 rasengan kernel: [15455.883104] PPP Deflate Compression module registered
Apr  8 03:02:19 rasengan pppd[18464]: local  IP address 70.3.25.90
Apr  8 03:02:19 rasengan pppd[18464]: remote IP address 68.28.185.69
Apr  8 03:02:19 rasengan pppd[18464]: primary   DNS address 68.28.186.91
Apr  8 03:02:19 rasengan pppd[18464]: secondary DNS address 68.28.178.91
```

---

### Post by apart on 2008-04-08
Hello,
I'm having similar problems with my dell 5505 (novatel hsdpa eu740) internal wwan. Same error from pppd.
Using minicom I can issue AT commands to the modem and I get responses.
What seems strange to me is
1) the AT+CSQ command returns 99,99 - as if there was no wireless signal available (I have the same symptom)
2) the AT+cops=? command locks my modem - I can't issue AT command anymore and have to poweroff to make it usable again

I'm curious if you guys can help me figuring something out. this is very important to me.

thanks,
andrew

---

### Post by apart on 2008-04-08
> **barichardson5727 said:**
>  I know that you have to initially activate the card in windows before it can be used in Linux.


what do you mean activate on windows? does it have to be done on the same computer?

---

### Post by nowhere@cox.net on 2008-04-08
The first time you use the card, it has to be registered/activated with your provider.  Basically it attaches your device to your account. The software to do this activation for Sprint  requires it's running on a windows machine. After this activation, you can use it on any system with drivers supporting your device.

If you buy your device from some place like 3gstore.com, they can activate it with your account for you.

Eric

---

### Post by nowhere@cox.net on 2008-04-08
By the way: I need a little help. My Novatel U727 has a built in microSD reader. Right now I need to 
```
modprobe -r airprime; 
modprobe -r usbserial; 
modprobe usbserial vendor=xxxx product=xxxx;
modprobe airprime
```
anytime I want to be able to access it. Each one requires sudo. How is the best way to automate this at boot/login?

Thanks,
Eric

---

### Post by barichardson5727 on 2008-04-09
If you want to load the modules at boot you can probably do the following:

make the file: /etc/modprobe.d/usbserial with this entry:
```
options usbserial vendor=0xXXXX product=0xXXXX
```

Then add the entries "usberial" and "airprime" to /etc/modules. When you reboot you should be able to connect.

---

### Post by apart on 2008-04-09
Simply throw those modules into the /etc/modules file.
Any options should probably go to /etc/modprobe.d/options.

---

### Post by mk4umha on 2008-05-10
Did anyone get the 5520 working in 8.04? I'm stuck at

```
Could not determine remote IP address: defaulting to 10.64.64.64

```

I'm using the airprime module and ATT wireless. Any help would be appreciated!

---

### Post by frisket on 2008-06-23
> **barichardson5727 said:**
> I figured this may be helpful, here is the output that I get upon a successful connection. You can compare this tor your output. I dont think that "pppd[6815]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received" is where your problem is, as I get the same output on a successful connection.

I think there must be something to it, however (I get the same problem), as it's precisely at that point that it fails. I'm using a friend's Three modem, and with assorted chat and peers scripts from the web it connects and authenticates, but even with noccp in the ppp config, the moment it tries a ConfReq it fails on this message and the connection hangs up.

> **barichardson5727 said:**
> Have you tried to make a connection from Windows? I know that you have to initially activate the card in windows before it can be used in Linux.

In my case the modem was originally set up (successfully) on a Windows box. My colleague has been using it successfully on a Mac (but oddly, it's failing there too now, although I haven't looked at the logs there yet to see what it's doing: the Mac interface is somewhat opaque about where it logs stuff to, if anywhere.

Would you be able to post the peers and chat scripts you use to make your successful connection (and your ppp/config if there's anything non-default in it); or email it to me if you prefer?

---

### Post by motin on 2008-06-24
> **Martin Nilsson said:**
> I have a Dell Wireless 5520 Generic Mobile Broadband 3G HSDPA, Expedite EU870D Minicard  build in my XPS M1330.

Now I would like to use Ubuntu as operating system and I can't find a driver for the Mobile Broadband to install?

/Martin

Is everything working as expected? Did the guide ([http://ubuntuforums.org/archive/index.php/t-461991.html](http://ubuntuforums.org/archive/index.php/t-461991.html)) do the trick?

Cheers

---

### Post by motin on 2008-06-25
> **apart said:**
> Simply throw those modules into the /etc/modules file.
Any options should probably go to /etc/modprobe.d/options.

Thanks. I threw usbserial into /etc/modules and the vendor/product options into the other file and the modem is now recognized correctly upon boot. Haven't tried suspending/resuming but hopefully it will work out in some way...

> **mk4umha said:**
> Did anyone get the 5520 working in 8.04? I'm stuck at

```
Could not determine remote IP address: defaulting to 10.64.64.64

```

I'm using the airprime module and ATT wireless. Any help would be appreciated!

I get the same error message as you but it has never been any problem surfing the internet nevertheless. I don't think the message is related to a modem issue. Cheers

---

### Post by motin on 2008-07-24
> **nowhere@cox.net said:**
> Just an FYI for anyone reading this thread. You can use the airprime driver instead of usbserial to possibly more than triple your download speeds. I am using a Novatel U727 USB card and previously I was using the very popular usbserial fix to connect at 500-600kbps.  I have since recompiled the airprime driver and my speeds tripled. There is one line in the driver source you need to add with the vendor and product code of your device. Then you can recompile just the airprime driver and copy it over the standard Gutsy one. 

In my case, the U727 has a microSD slot as well so I have to load the usbserial module with the vendor and product code, then load my new airprime driver then I am good to go at 2100kbps. 

[[IMG]http://www.speedtest.net/result/254397676.png[/IMG]](http://www.speedtest.net) 

If there is interest and I can find time I can make a HOWTO...

Cheers,
Eric

> **barichardson5727 said:**
> ok...so I have mine working now with the airprime modules. I noticed a huge difference immediately. Here is a link to some pretty good step by step instructions for using the airprime modules:
[http://ubuntuforums.org/archive/index.php/t-461991.html](http://ubuntuforums.org/archive/index.php/t-461991.html)

Thanks guys - airprime is definitely the module to use! I have updated that guide for Hardy - thanks again!

---

