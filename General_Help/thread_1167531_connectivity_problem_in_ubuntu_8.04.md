---
title: "connectivity problem in ubuntu 8.04"
date: 2009-05-23
forum: General Help
---

### Post by ahmedajaz on 2009-05-23
I got an Internet connection from BSNL  i.e a WLL connection..
 and this was the steps which i  should perform to connect to internet in ubuntu 8.04
  
 Prerequisites: A BSNL Fixed Wireless Phone with a serial to USB cable, with internet access enabled on that phone. Install the wvdial and pppd packages if they are not already installed.
 General Information: With the above mentioned phone, current package available for internet access is Rs. 250 per month for unlimited access (March 2008), however, the phone is blocked while internet is used. It is a good idea to be as close to the BSNL tower/exchange to get good data transfer speeds.
 Actual Configuration:
 1.Plug the USB cable in to one of the USB sockets of the computer. Remember which socket the cable was plugged into.
 2.Run the command
 sudo wvdialconf
 3.Edit /etc/wvdial.conf (with sudo) to look like the following file:
 [Dialer Defaults]
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 Init3 = at+crm=1;+cmux=1;+cps=33;+cta=0
 Modem Type = Analog Modem
 Baud = 115200
 New PPPD = yes
 Modem = /dev/ttyUSB0
 Idle Seconds = 90
 Auto Reconnect = off
 ISDN = 0
 Phone = #777
 Password=cdma
 Username=cdma
 4.Please see to it that the settings in the AirTone800 phone are also for 115200 baud, if they are not, then no connections will be made.
 5.Please add in the /etc/sudoers file in the section a line like
 # User privilege specification
 username machine_name = NOPASSWD: /usr/bin/wvdial, /usr/bin/killall
 on my machine, this line looks like:
 moz t64c = NOPASSWD: /usr/bin/wvdial, /usr/bin/killall
 The above line allows the use of wvdial and killall commands as sudo without asking for a password.
 6.At a command prompt, type wvdial to connect to the internet. You should see an output like the following. Please note that &#8220;Caught signal 2: Attempting to exit gracefully&#8230;&#8221; line comes after pressing Ctrl+C to disconnect from the internet.
 moz@t64c:~$ wvdial
 WvDial<*1>: WvDial: Internet dialer version 1.56
 WvModem<*1>: Cannot get information for serial port.
 WvDial<*1>: Initializing modem.
 WvDial<*1>: Sending: ATZ
 WvDial Modem<*1>: ATZ
 WvDial Modem<*1>: OK
 WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 WvDial Modem<*1>: OK
 WvDial<*1>: Sending: at+crm=1;+cmux=1;+cps=33;+cta=0
 WvDial Modem<*1>: at+crm=1;+cmux=1;+cps=33;+cta=0
 WvDial Modem<*1>: OK
 WvDial<*1>: Modem initialized.
 WvDial<*1>: Sending: ATDT#777
 WvDial<*1>: Waiting for carrier.
 WvDial Modem<*1>: ATDT#777
 WvDial Modem<*1>: CONNECT
 WvDial<*1>: Carrier detected. Waiting for prompt.
 WvDial Modem<*1>: ~[7f]}#@!}!/} }3}&#8221;}&} } } } }#}%B#}%}&#8217;}&#8221;}(}&#8221;g}(~
 WvDial<*1>: PPP negotiation detected.
 WvDial<Notice>: Starting pppd at Sun Mar 23 10:14:55 2008
 WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
 WvDial<Err>: &#8211;> PAP (Password Authentication Protocol) may be flaky.
 WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
 WvDial<Err>: &#8211;> CHAP (Challenge Handshake) may be flaky.
 WvDial<Notice>: Pid of pppd: 6006
 WvDial<*1>: Using interface ppp0
 WvDial<*1>: local IP address 10.1.0.77
 WvDial<*1>: remote IP address 10.64.64.64
 WvDial<*1>: primary DNS address 218.248.240.208
 WvDial<*1>: secondary DNS address 218.248.240.135
 Caught signal 2: Attempting to exit gracefully&#8230;
 WvDial<*1>: Terminating on signal 15
 WvDial<*1>: Connect time 5.8 minutes.
 WvDial<*1>: Disconnecting at Sun Mar 23 10:20:51 2008
 7.If you would have another shell prompt open where you run the tail -f /var/log/messages command, then you should see an output similar to:
 moz@t64c:~$ tail -f /var/log/messages
 Mar 23 10:14:55 t64c pppd[6006]: pppd 2.4.4 started by michael, uid 1000
 Mar 23 10:14:55 t64c kernel: [ 428.560949] PPP generic driver version 2.4.2
 Mar 23 10:14:55 t64c pppd[6006]: Using interface ppp0
 Mar 23 10:14:55 t64c pppd[6006]: Connect: ppp0 <&#8211;> /dev/ttyUSB0
 Mar 23 10:14:59 t64c pppd[6006]: CHAP authentication succeeded
 Mar 23 10:14:59 t64c pppd[6006]: CHAP authentication succeeded
 Mar 23 10:14:59 t64c kernel: [ 432.128610] PPP BSD Compression module registered
 Mar 23 10:14:59 t64c kernel: [ 432.175440] PPP Deflate Compression module registered
 Mar 23 10:15:03 t64c pppd[6006]: Could not determine remote IP address: defaulting to 10.64.64.64
 Mar 23 10:15:03 t64c pppd[6006]: local IP address 10.1.0.77
 Mar 23 10:15:03 t64c pppd[6006]: remote IP address 10.64.64.64
 Mar 23 10:15:03 t64c pppd[6006]: primary DNS address 218.248.240.208
 Mar 23 10:15:03 t64c pppd[6006]: secondary DNS address 218.248.240.135
 Mar 23 10:20:51 t64c pppd[6006]: Terminating on signal 15
 Mar 23 10:20:51 t64c pppd[6006]: Connect time 5.8 minutes.
 Mar 23 10:20:51 t64c pppd[6006]: Sent 134918 bytes, received 511250 bytes.
  
 But..
 the problem which i faced was..
 ahmed@ahmed-desktop:~$ wvdial
 &#8211;> WvDial: Internet dialer version 1.60
 &#8211;> Cannot open /dev/usbdev2.1_ep00: Permission denied
 &#8211;> Cannot open /dev/usbdev2.1_ep00: Permission denied
 &#8211;> Cannot open /dev/usbdev2.1_ep00: Permission denied
  
 please help me in this&#8230;

HW TO FIND OUT THE NAME OF PORT MY MODEM IS ATTACHED TO.?

---

### Post by GeorgeVita on 2009-05-23
Hi **ahmedajaz**,

When a new peripheral is attached to the PC, the system try to recognize it and assign a "driver" to communicate with it. Most times using a USB modem, the communication ports created are: **/dev/ttyUSBx** or **/dev/ttyACMx** where **x** is a number (0, 1, 2, ...).

To find your modem port do the following:

Boot without the modem, wait for the system to stabilize, attach the modem, wait 20 seconds, open a terminal window and try:

[B]dmesg
lsusb
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*[/B]

Post here _the last 10-15 lines of dmesg_ (concerning /dev/ttyUSBx and usbserial) and also the output of the other two commands.

The **dmesg** command will show all system activity after inserting the modem, **lsusb** will show all USB peripherals attached and their vendor/product IDs and **ls /dev/tty...** will list any configured serial communication ports.

Regards,
George

---

