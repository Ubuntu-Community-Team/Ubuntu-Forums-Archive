---
title: "Dell mobile broadband (Verizon) - stuck on configuration"
date: 2007-06-09
forum: Dell  Ubuntu Support
---

### Post by stonecutter on 2007-06-09
Hello 
I have a Dell mobile broadband card which I'm trying to install on my XPS1210. I followed the instructions from [http://www.savvyadmin.com/2007/06/03/ubuntu-dell-5700-evdo/](http://www.savvyadmin.com/2007/06/03/ubuntu-dell-5700-evdo/) 
with no luck (yet!). I think part of my problem is here- 

lsusb

Bus 005 Device 003: ID 046d:08c6 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 006: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 004: ID 413c:8126 Dell Computer Corp. 
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 413c:8114 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  

grep tty /var/log/messages

Jun  8 18:34:10 WDIXPS kernel: [ 1696.544000] usb 3-2: generic converter now attached to ttyUSB0
Jun  8 18:34:10 WDIXPS kernel: [ 1696.544000] usb 3-2: generic converter now attached to ttyUSB1
Jun  8 21:05:55 WDIXPS kernel: [   15.828000] usb 3-2: generic converter now attached to ttyUSB0
Jun  8 21:05:55 WDIXPS kernel: [   15.832000] usb 3-2: generic converter now attached to ttyUSB1
Jun  8 21:08:15 WDIXPS pppd[6063]: Connect: ppp0 <--> /dev/ttyUSB0
Jun  8 21:12:52 WDIXPS pppd[6469]: Device ttyUSB0 is locked by pid 6063


my /etc/ppp/peers/verizon file:

hide-password 
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/verizon"
debug
/dev/ttyUSB0
115200
defaultroute
noipdefault 
user "xxxyyy7426@vzw3g.com"
remotename verizon
ipparam verizon

usepeerdns
lcp-echo-failure 0
lcp-echo-interval 0

***

I have the onboard wireless, looks to using eth1, as my ifconfig shows my 172.16.x.x subnet and I've been able to successfully use that card. 

Any thoughts? A bit of a noob, but willing to learn. thanks.

---

### Post by LinuxCruiser on 2007-06-24
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1


Did you ever get your card working? From your output, it looks like
you're pretty much there.

To test, disable networking from Network Manager, and perform an
ifconfig to ensure that you have no other interface up.

Now try to connect manually by issuing the following command:

$ pppd call verzion

$ tail /var/log/messages

Should tell you how it's progressing in the connection. If
successfully connected, you will see a ppp0 interface in the output of
ifconfig.

$ ifconfig ppp0

If you continue to have troubles, you also should make sure that the
card actually works in Windows. These cards are required to go
through an activation process which will prevent it from used on the
Verizon network until completed.

Regards...

GM


-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFGfyBnBZd5UQddvKkRAjWFAJ9ZLNLUUDBFKwQ5ASOt8BF0BxpAYACgtR1Z
JmWfbllAk18b9jCTAyUWkAY=
=FXFJ
-----END PGP SIGNATURE-----

---

### Post by topshop on 2008-07-08
my dell dimension was stolen and has id where if someone was to create or start ISP internet it would be possible to see when turned on?:(

---

