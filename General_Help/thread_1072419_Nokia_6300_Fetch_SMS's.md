---
title: "Nokia 6300: Fetch SMS's"
date: 2009-02-17
forum: General Help
---

### Post by tom66 on 2009-02-17
I have searched in many places, but I cannot find what I am looking for. I need to get the SMS messages from the Inbox (and any other folders) off a Nokia 6300 phone. Other features are optional extras. 

Thanks.

---

### Post by papatrexas on 2009-03-10
My friend, I have the exact problem! I am running Wammu on an HP Pavilion DV5-1130ev and can't download nor messages neither notes from my phone
:(:(:(

---

### Post by debiant on 2010-05-30
Me too-Wammu can't read them, it doesn't have permission apparently.  I've tried both "nokia"mode and "dat storage" modeon the phone using a USB cable.  Does anyone know of any software that can do this?

PS also tried gnokii, can't even detect the phone

---

### Post by debiant on 2010-05-30
KmobileTools can't read it either.  Guess this is one for the "why you can't get rid of windows yet" list.  
:(
I have another HD with XP on it for these things. 

Does anyone know a mobile phone that is Ubuntu compatible?

---

### Post by pkot on 2010-07-10
Which gnokii version do you use? That should be supported since gnokii 0.6.27. To have the most bugs removed make sure that you use 0.6.29 (it might not be available as ubuntu package).

---

### Post by bjorn2die on 2010-07-26
I just tested this with my 6300 and 0.6.30git and I'm not getting any SMS messages either. Sending worked like a charm.
```
gnokii --identify
GNOKII Version 0.6.30git
IMEI         : 358051xxxxxxxxx
Manufacturer : Nokia
Model        : Nokia 6300
Product name : Nokia 6300
Revision     : V 05.00
```

```
gnokii --getsms ME 1 end
GNOKII Version 0.6.30git
LOG: debug mask is 0x1
LOG: rlpdebug mask is 0x1
Config read from file /home/bjorn/.config/gnokii/config.
phone instance config:
model = AT
port = /dev/ttyACM0
connection = serial
initlength = default
serial_baudrate = 19200
serial_write_usleep = 10000
handshake = software
require_dcd = 0
smsc_timeout = 10
rfcomm_channel = 0
sm_retry = 1
Initializing AT capable mobile phone ...
Serial device: opening device /dev/ttyACM0
Serial device: setting RTS to high and DTR to high
Message sent: 0x00 / 0x0004
41 54 5a 0d                                     | ATZ
write: [ATZ<cr>]
read : [ATZ<cr><cr><lf>OK<cr><lf>]
Message received: 0x00 / 0x000a
02 41 54 5a 0d 0d 0a 4f 4b 0d                   |  ATZ   OK
Received message type 00
Message sent: 0x00 / 0x0005
41 54 45 31 0d                                  | ATE1
write: [ATE1<cr>]
read : [ATE1<cr><cr><lf>OK<cr><lf>]
Message received: 0x00 / 0x000b
02 41 54 45 31 0d 0d 0a 4f 4b 0d                |  ATE1   OK
Received message type 00
Message sent: 0x00 / 0x000a
41 54 2b 43 4d 45 45 3d 31 0d                   | AT+CMEE=1
write: [AT+CMEE=1<cr>]
read : [AT+CMEE=1<cr><cr><lf>OK<cr><lf>]
Message received: 0x00 / 0x0010
02 41 54 2b 43 4d 45 45 3d 31 0d 0d 0a 4f 4b 0d |  AT+CMEE=1   OK
Received message type 00
Message sent: 0x06 / 0x0007
41 54 2b 47 4d 4d 0d                            | AT+GMM
write: [AT+GMM<cr>]
read : [AT+GMM<cr><cr><lf>Nokia 6300<cr><lf><cr><lf>OK<cr><lf>]
Message received: 0x06 / 0x001b
02 41 54 2b 47 4d 4d 0d 0d 0a 4e 6f 6b 69 61 20 |  AT+GMM   Nokia
36 33 30 30 0d 0a 0d 0a 4f 4b 0d                | 6300    OK
Received message type 06
Message sent: 0x06 / 0x0008
41 54 2b 43 47 4d 49 0d                         | AT+CGMI
write: [AT+CGMI<cr>]
read : [AT+CGMI<cr><cr><lf>Nokia<cr><lf><cr><lf>OK<cr><lf>]
Message received: 0x06 / 0x0017
02 41 54 2b 43 47 4d 49 0d 0d 0a 4e 6f 6b 69 61 |  AT+CGMI   Nokia
0d 0a 0d 0a 4f 4b 0d                            |     OK
Received message type 06
Message sent: 0x63 / 0x0009
41 54 2b 43 53 43 53 3f 0d                      | AT+CSCS?
write: [AT+CSCS?<cr>]
read : [AT+CSCS?<cr><cr><lf>+CSCS: "PCCP437"<cr><lf><cr><lf>OK<cr><lf>]
Message received: 0x63 / 0x0023
02 41 54 2b 43 53 43 53 3f 0d 0d 0a 2b 43 53 43 |  AT+CSCS?   +CSC
53 3a 20 22 50 43 43 50 34 33 37 22 0d 0a 0d 0a | S: "PCCP437"
4f 4b 0d                                        | OK
Received message type 63
Initialisation completed
Message sent: 0x1a / 0x000a
41 54 2b 43 50 4d 53 3d 3f 0d                   | AT+CPMS=?
write: [AT+CPMS=?<cr>]
read : [AT+CPMS=?<cr><cr><lf>+CPMS: (),(),()<cr><lf><cr><lf>OK<cr><lf>]
Message received: 0x1a / 0x0023
02 41 54 2b 43 50 4d 53 3d 3f 0d 0d 0a 2b 43 50 |  AT+CPMS=?   +CP
4d 53 3a 20 28 29 2c 28 29 2c 28 29 0d 0a 0d 0a | MS: (),(),()
4f 4b 0d                                        | OK
Received message type 1a
strings[0] =
strings[1] = (null)
strings[2] = (null)
strings[3] = (null)
Ignoring unknown memory type "".
Getting message #1 from ME
Message sent: 0x00 / 0x000d
41 54 2b 43 50 4d 53 3d 22 4d 45 22 0d          | AT+CPMS="ME"
write: [AT+CPMS="ME"<cr>]
read : [AT+CPMS="ME"<cr><cr><lf>ERROR<cr><lf>]
Message received: 0x00 / 0x0016
03 41 54 2b 43 50 4d 53 3d 22 4d 45 22 0d 0d 0a |  AT+CPMS="ME"
45 52 52 4f 52 0d                               | ERROR
Received message type 00
Getting SMS failed (location 1 from ME memory)! (Unknown error - well better than nothing!!)
Serial device: closing device
```

---

