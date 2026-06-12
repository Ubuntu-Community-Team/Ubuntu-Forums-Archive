---
title: "How do I get my nokia 2112 phone with the ca-42 usb adapter to work?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by solarwind on 2006-06-24
Hello everyone,

I have a nokia 2112 phone with the ca-42 usb adapter and I can use it as a modem to connect to the internet on windoze. How do I do this on Linux? I probably need:

- CA-42 usb cable adapter
- Nokia 2112 modem driver

But I can't find a solution anywhere. Can someone please help me? 

Thanks!

---

### Post by loell on 2006-06-24
sorry, there were many who tried looking for solutions with nokia cable connectivity on linux but failed, there isn't just any driver provided by nokia to linux, sadly, it just works with windows

---

### Post by solarwind on 2006-06-29
[QUOTE=loell]sorry, there were many who tried looking for solutions with nokia cable connectivity on linux but failed, there isn't just any driver provided by nokia to linux, sadly, it just works with windows[/QUOTE]

Psssh. Yeah. It doesn't work on windoze either half the time.

Lol. Nokia is garbage when it comes to data calls.

---

### Post by Feisty-Fox on 2007-08-25
This hardware is known to work on Puppy Linux 2.14.  I have personally tested it and got the connection up and running for my Reliance India Mobile Phone (Nokia 2112) connected to the PC through a CA42 data cable.  I, however, could not get it running on Mandrake 10.0, Mepis and Knoppix 5.0.  If anyone's interested, I shall the post the entire procedure (it's a bit lengthy) in this forum.  I hope that with a little bit of tweaking, I should be able to get it running on Ubuntu Feisty Fawn as well.

BTW dear newbies,  back here in Linux country we don't talk of drivers - we use the term "modules" instead.

Tehehehe

---

### Post by loell on 2007-08-25
well, duh! a lot had happened since this post, the obex protocol had improved in great magnitude, and many nokia phones especially the current ones are compatible with it.

and we also talk drivers not just modules.

---

### Post by Feisty-Fox on 2007-08-27
The following post should help you get your Ubuntu Feisty Fawn system connected to the internet using a Nokia 2112 CDMA mobile phone and a CA42 USB data cable.  I have been able to establish a successful connection to my ISP from a Ubuntu 7.04 (Feisty Fawn) system using wvdial v1.56.

I have made this post a bit more elaborate than necessary for the benefit of new Linux users.  It is presumed that a data plan for your mobile phone has been activated by your ISP.  

1] Connect the usb end of your CA42 data cable to the PC and the other end to the Nokia 2112's pop-port connector.  Upon connecting, your phone should display the message "Ready for data". If you do not get this message while connecting the phone end of the data cable to the phone's pop-port, remove and plug it back again.  You may have to repeat this a couple of times to get the desired result.

2] Boot into your Ubuntu system with the CA42 data cable and Nokia 2112 connected.

3] Open a shell window, type the command "dmesg | grep -i usb" and hit Enter (without the quotes, that is).  You should be able to see something similar to the following: -

	[   23.648000] usb 1-2: ark3116 converter now attached to ttyUSB0
	[   23.648000] usbcore: registered new interface driver ark3116

If this is the case, your hardware has been recognised by your system, the appropriate module  loaded and the device made available for your use at /dev/ttyUSB0. If your hardware is not been recognised, you may have to manually load the relevant kernel module by entering the command "modprobe usbserial vendor=0x6547 product=0x0232".  You can now proceed to soft link it to /dev/modem. 

3] Become root, type the command "ln -s /dev/ttyUSB0 /dev/modem" and hit enter.  (To check if the soft link has been made, you can issue the command "file /dev/modem" - you should get the response "/dev/modem: symbolic link to `/dev/ttyUSB0'".

4] The next step would be to check if your Ubuntu system and the Nokia 2112 are on talking terms.  We will use the wvdial utility to confirm this.  While still being root, type the command "wvdialconf 2112.conf" and hit enter.  You should get a response as follows: -

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttyUSB0 first, /dev/modem is a link to it.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- ERROR
ttyUSB0<*1>: Speed 4800: AT -- ï¿½
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- 
ttyUSB0<*1>: Speed 460800: AT -- [06]ï¿½
ttyUSB0<*1>: Speed 460800: AT -- 
ttyUSB0<*1>: Max speed is 230400; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   

Found a modem on /dev/ttyUSB0, using link /dev/modem in config.
2112.conf<Warn>: Can't open '2112.conf' for reading: No such file or directory
2112.conf<Warn>: ...starting with blank configuration.
Modem configuration written to 2112.conf.
ttyUSB0<Info>: Speed 230400; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

The first couple of lines confirm that the system and the Nokia 2112 are indeed on talking terms and a configuration file "2112.conf" is created in your home directory by the wvdialconf utility.  Now that things are looking up, it is time to create a .ppprc file in your home directory.  

5] Open your favourite text editor and the type the following line, replacing the hash (#) symbols with whatever username and password is required by your ISP.

user ######## password ########

Save the file as .ppprc in your home directory. The pppd utility may require this file later when it attempts to establish a connection with your ISP.

6] Using your favourite text editor again, open the 2112.conf file (created earlier on by the wvdialconf utility), delete the entire contents and paste the following lines into it, taking care to replace the phone number, username and password fields with whatever your ISP requires you to: -

[Dialer Defaults]
Init1 = AT
Init2 = AT+CRM=1
Init3 = AT+CSO=33
Init4 = ATE0V1
Init5 = AT
Init6 = ATS0=0
Modem Type = Analog Modem
Phone = #777
ISDN = 0
Password = 9360685907
Username = 9360685907
Modem = /dev/modem
Baud = 115200
Stupid Mode = 1 

This is how my configuration file looks like.  My ISP (Reliance India Mobile) requires me to dial the number #777 and use my phone number for both the username and password fields.  Yours would be different and you will have to change the Phone, Password and Username fields according to your ISP's requirements.  (For those interested, the 6 init strings shown above are the ones used by a Windows XP system to negotiate a connection).  When you are done, save the file to the same location i.e., your home directory.

7] We now move on to attempt a connection to the ISP.  Type the command "wvdial -C 2112.conf" and hit enter.  You should get to see a flurry of "OK"s followed by a lot of garbage (non-printing characters). Well, your connection has been established.  You can now minimise this shell window.  (you need to maximise it again later to terminate the connection by hitting Ctrl-C.)  To see if your connection is working, open another shell window and enter the command "ping google.com", or better still "ping ubuntu.com"  You should be able to see continuous responses to your ping command.  

It's now time to exit your "ping window" and fire up your browser - Mozilla Firefox, that is.

anandkumarvj [at] rediffmail.com

---

