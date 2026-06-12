---
title: "Samsung phone as modem?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by quietglow on 2005-11-10
I'm not sure this is where this belongs but I've wondered this for some time:

I have a Samsung cell phone that I have connected with my OSX laptop via a usb cable. Using Verizon's express network (free except it uses your minutes) I can actually dial up a decent wireless connection--14k or so. I've done this on a windows box as well, though unlike the mac I had to install drivers. 

SO...where would I even begin getting this to work with my fantastic Ubuntu lappy? I have lots of specifics about phone model and the connecting parameters, but if this has been covered somewhere else, I don't want to mess with posting it all. Anyone else do this?

---

### Post by adwait on 2005-11-11
There's gotta be a linux driver for the samsung phone....you'll have to get that. If you can get that, then use used gPPP to setup a normal dial up connection.

---

### Post by quietglow on 2005-11-11
Okay, I've been hunting around and found that what I need to do is treat it like a USB modem essentially. Most places that suggest they are getting it to work are using the acm module. It doesn't appear that one of those is installed by defult, but a cdc-acm module is--and I found a couple of instances of this working for people trying to get USB modems working.

BUT, when I plug the phone in, I'm seeing (dmesg and lsmod) that it is being recognized as a Visor and causing the usbserial module to be loaded on "USB3". Thats good right?! If I can just find a way to get the phone assigned to one of the serial ports (tty) I should be able to set up a regular old ppp connect pppconfig or something.

Anyone have any clues?

---

### Post by quietglow on 2005-11-11
Sorry, scratch that: the phone is connected on ttyUSB3 which sounds like it would be really good, but when I set up a dial up in the network pane I get this in my dmesg when I try to activate it:

[4300202.525000] visor ttyUSB3: Device lied about number of ports, please use a lower one.

I tried putting ttyUSB1 as the modem location, and it gives the same message.

---

### Post by jimbob on 2005-11-11
I believe that the cdc-acm module IS the acm module.

Ubuntu sees my USB modem as /dev/ttyACM0.    Have you tried that?

---

### Post by quietglow on 2005-11-11
Okay, more digging and I found this:

[http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=450](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=450)


SO tempting, yet it doesn't work: I don't ever get either a /dev/ttyACM0 or a /dev/usb/ttyACM0

I just tried making a /dev/ttyACM0 by mknod /dev/ttyACM0 c 166 0 

It still doesn't work. I think the problem is that its being picked up as a visor and shuffled over to /dev/USB3 where it can't do its work. Seems like if it was getting picked up properly by the acm mod it would have made the ttyACM0 itself, right?

---

### Post by sidd-tx on 2006-02-23
Just giving a little nudge....

Having the same problem. I have a Samsung SCH-i730, and would LOVE to use the EVDO network with Ubuntu. 

Running 5.10 with 2.6.12-10-386 kernel. 

When plugging in the USB cable, dmesg indicates the device has been assigned to ttyUSB0 usually, but sometimes it hits ttyUSB1 or ttyUSB2, just changes once in a while.

How do I get the device assigned to /dev/ttyACM0 or /dev/usb/ttyACM0  ???

I've look around this forum and linuxquestions.org as well. If I have missed it, which is totally possible, can someone please lend a helping hand?

---

### Post by sidd-tx on 2006-02-23
Answered my own question....  Just took some more googling...

I had to first modprobe the following modules:
uhci (gave an error: "FATAL: Module uhci not found")  Not sure about this..
usbserial
ftdi_sio
cdc-acm

Then, on the Samsung, I had to go into the phone app and punch in **7284 and set the data connection through USB..

Plugged the phone in via USB, and magic...  The phone was now /dev/ttyACM0...!!

but after following the instructions from this site:
[http://www.linuxquestions.org/linux/answers/Networking/Verizon_Cell_Phone_Internet](http://www.linuxquestions.org/linux/answers/Networking/Verizon_Cell_Phone_Internet)

I still cannot get Ubuntu to connect. No errors in dmesg or on the GUI, and nothing on the phone screen..

Can anyone give any further assistance?

---

### Post by quietglow on 2006-02-23
I'm now on a different phone: a v3 Razr. It, of course, has a usb port and also shows up as /dev/ttyACM0.

 Like you, I haven't been able to get it to dial, but I am thinking that this may be something actually blocked in the phone. If I plug it into a Mac, it is immediately recognized as a modem (as my samsung was) but it gives an error when I attempt to dial out (which my samsung never did).

---

### Post by sidd-tx on 2006-02-23
Actually. When I plugged my Samsung into a Mac, it was not only recognized, but I could connect to EVDO with it. I just created a new internet connection using the only verizon script in the menu, and specified the samsung device. (sorry about the vagueness, I don't have the Mac in front of me, so I'm just going off memory).

Ubuntu recognizes it ( I think - dmesg has it as a handspring visor ) but I cannot tell if Ubuntu cannot communicate with the modem or if there is something else wrong..

At least I can connect with my iBook...  But it would be just too cool to connect my Ubuntu machines...!

---

### Post by quietglow on 2006-02-23
Yeah, Ive been dialing in via an iBook for 3 years--it used to really make a stir when I'd do it at a Starbucks a few years ago. I've actually bought and downloaded an entire album from ITMS while riding in a car :-) No really!

My razor doesn't work, though, and I'm guessing its becasue Verizon has intentionally crippled it. I suppose I could google up some answers but the ipod is the focus for me these days :-)

When I need the mobile internet now I grab my wife's cell (a samsung) and ibook and I'm set.

---

### Post by sidd-tx on 2006-02-23
Looked at your wiki...  I can see why that is taking most of your time. I too can appreciate your efforts, as I have a 5G iPod. But I use my Mac to manage that bad boy. 

In the mean time, if anyone can help me get one of my Ubuntu machines connected to Verizon Wireless with my samsung, I would greatly appreciate it..


Thanks all..

---

### Post by Digidiz on 2006-02-23
isnt using mobile phones tad expensive????

---

### Post by sidd-tx on 2006-02-23
Well, it depends on what you consider expensive.  I pay $44 a month for unlimited data, but I have to do that for work purposes anyway.  It's just nice to be able to connect my laptop while on the road using an ISP I already pay $$ for.

---

