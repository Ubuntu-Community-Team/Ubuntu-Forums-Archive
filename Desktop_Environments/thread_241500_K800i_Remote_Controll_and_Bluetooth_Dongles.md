---
title: "K800i Remote Controll and Bluetooth Dongles"
date: 2006-08-22
forum: Desktop Environments
---

### Post by lazerradial2003 on 2006-08-22
I've just purchased the Sony Ericson K800i phone and have been reading about its remote control features, on a windows PC it can be used to control things like music playback and so-on over bluetooth. I was wondering what experiance people have of getting things like this to work on (k)ubunutu or what people thought the chances were of getting the windows apps to be useable through WINE or something? Any comments appreciated.

Also if anyone can reccomend a bluetooth dongle they have had success with through (k)ubuntu, ideally one of the cheaper ebay ones then i'd be grateful! Thanks, lazerradial2003.

---

### Post by lazerradial2003 on 2006-08-23
Any Suggestions anyone? The phones arriving later today so would really like to go ahead and buy a bluetooth dongle...

---

### Post by lazerradial2003 on 2006-08-24
Anyone?

---

### Post by perper on 2006-08-24
The k800i acts as a normal HID-compatible bluetooth mouse and keyboard. This means that the remote control function is supported (almost) out of the box in ubuntu. You have to enable HID in /etc/default/bluez-utils (the file is well documented).

Then just select the remote on you pc and it will search up your computer and connect. :)

I got my bluetooth dongle from ledshoppe.com, cost 6 dollars inkluding shipping from hong kong.

---

### Post by brujoand on 2007-01-01
this isnt working for me. Im not reallye comfertable with bluez yet.. i'v got my bluetooth mous working but i cant get the k800i remote control running, nor filetransfer between me laptop and my phone. anyone? ;)

---

### Post by brujoand on 2007-01-01
correction, the remote works perfect.. hcitool scan, and then hidd --connect btadress and the phone promtes me to know how i would like to use the remote.. oh oh oh.. this is sweet;)
 
but im still nowhere on the filetransfer.. :(

---

### Post by fuoco on 2007-01-05
Could you maybe give me a step by step instruction to get the remote working? thanks

---

### Post by themastaaska on 2007-10-07
I just got my new phone k800i. And i tried to follow your instructions. But from where do i get the file bluez-utils. I checkt if its in /etc/default/bluez-utils, but i only could find a file names "bluetooth". What now?

greetz tma

PS: Thx for your answers

---

### Post by tgalati4 on 2007-10-07
I used Salling's Clicker Bluetooth software on my Sony w810i and I can control iTunes on my powerbook under Mac OS X.  It works pretty well as an remote iTunes controller.

I have yet tried to get the same functionality under Ubuntu.  It would be nice to control Banshee 0.13.1 via blue tooth.

---

### Post by girard on 2007-11-02
> **GrimmVarg said:**
> correction, the remote works perfect.. hcitool scan, and then hidd --connect btadress and the phone promtes me to know how i would like to use the remote.. oh oh oh.. this is sweet;)
 
but im still nowhere on the filetransfer.. :(

try to look for Bluetooth File Sharing in synaptic. it has to be running when you send/receive files.

I have a different question though...

my remote control setup only works when ubuntu asks my phone to be used as a remote. i cannot establish the service from the phone though. i already added the address to /etc/default/bluexxx but i still can't get it to work. my k800i says that i have to check the settings of the pc because signal, connection, etc, are all ok. any ideas?

EDIT:

i got it... when you first establish the remote connection, do not disconnect or end the service when you enter hidd --server into the terminal and/or when you add the address to the /etc/default/XXXXX file. got mine to work this way.

---

