---
title: "USB serial adapter unreliable on startup"
date: 2011-03-08
forum: Desktop Environments
---

### Post by pk_naptown on 2011-03-08
[FONT=PrimaSans BT,Verdana,sans-serif]I am using a Sealink PN 2202 USB serial adapter on a linux box (Ubuntu 10.4) running kernel 2.6.32-28-generic. I have written a perl script to simply log the incoming RS232 data (9600 8N2) and it works fine when I start it from a bash shell: 

[/FONT][FONT=PrimaSans BT,Verdana,sans-serif]perl /home/pk/PerlCode/RS232_D4_v11.pl[/FONT]
[FONT=PrimaSans BT,Verdana,sans-serif]
However, I need the computer to boot and start logging after a POR. If I try to use Startup Manager to execute my script everything seems ok but I randomly loose about 20% of the incoming RS232 data. In Startup Manager I use the command 

[/FONT][FONT=PrimaSans BT,Verdana,sans-serif]gnome-terminal --title="D4 RS232 Log" --execute bash -c "perl
/home/pk/PerlCode/RS232_D4_v11.pl"[/FONT]
[FONT=PrimaSans BT,Verdana,sans-serif]
If I close the automatically-started script and restart it from a bash shell, I again will randomly loose about 20% of the incoming RS232 data. It almost seems like I have screwed up the driver by using the Startup Manager. The only way I can get reliable logging again is to remove the script from Startup Manager, then restart the computer and manually launch the perl script.

I was thinking that maybe the order in which the driver was loaded and perl script started might be an issue. So I tried a bash script that sleeps for 15seconds, then starts the perl script. Again, I loose random pieces of incoming data when this is initiated by Startup Manager.

Here is some more info:

[/FONT][FONT=PrimaSans BT,Verdana,sans-serif]lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0c52:2223 Sealevel Systems, Inc. 
Bus 002 Device 003: ID 0c52:2213 Sealevel Systems, Inc. 
Bus 002 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-Port Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/FONT][FONT=PrimaSans BT,Verdana,sans-serif]sudo cat /proc/tty/driver/usbserial
usbserinfo:1.0 driver:2.0
0: module:ftdi_sio name:"FTDI USB Serial Device" vendor:0c52
product:2213 num_ports:1 port:1 path:usb-0000:00:1d.0-2.1
1: module:ftdi_sio name:"FTDI USB Serial Device" vendor:0c52
product:2223 num_ports:1 port:1 path:usb-0000:00:1d.0-2.2[/FONT]
[FONT=PrimaSans BT,Verdana,sans-serif]
[/FONT][FONT=PrimaSans BT,Verdana,sans-serif]ls -al /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2011-03-08 09:56 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2011-03-08 09:56 /dev/ttyUSB1

[/FONT][FONT=PrimaSans BT,Verdana,sans-serif]I am a member of the group dialout.[/FONT]

I though it may have something to do with su vs my ownership of files....
[FONT=PrimaSans BT,Verdana,sans-serif]If I do a sudo chmod 777 /dev/ttyUSB* then 

ls -al /dev/ttyUSB*
crwxrwxrwx 1 root dialout 188, 0 2011-03-08 09:56 /dev/ttyUSB0
crwxrwxrwx 1 root dialout 188, 1 2011-03-08 09:56 /dev/ttyUSB1

However, after rebooting it reverts to 

ls -al /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2011-03-08 09:56 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2011-03-08 09:56 /dev/ttyUSB1[/FONT]

If anyone can suggest some way to solve this I would greatly appreciate it

Thanks, pk

---

### Post by pk_naptown on 2011-03-11
I figured out the solution. Start the script using cron @reboot. For some reason starting the script using Startup Application Manager screwed up the driver (maybe an ownership issue?). 

Phew......

---

