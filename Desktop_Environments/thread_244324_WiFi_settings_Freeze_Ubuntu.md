---
title: "WiFi settings Freeze Ubuntu"
date: 2006-08-26
forum: Desktop Environments
---

### Post by dave martin on 2006-08-26
Can any one help me?
I'm totally new to Linux, but I sucessfully loaded Dapper drake and its running well. Got the ethernet connection working straight away.
I need the unit to go down the garden so I need to use my wifi connection.
I go into System, Administration, networking, wireless connection, properties.
In the ESSID drop down it lists my network an a neighbours, I input all the usual details including the WEP key,set it to DHCP then click ok, then activate then the computer freezes and I have to re-boot.
I've tried it with the ethernet connection disabled but still the same.
Any one have some idea or is it a bug?
I don't really want to run 100+ feet of CAT5 down the garden when I know that the WiFi easily makes it.

Thanks in advance,
Dave

---

### Post by superD on 2006-08-27
What are your system specs? I have this problem with my PC, but believe it may be due to it's fairly low-grade hardware. I really need help with this one too :(

---

### Post by insyzygy on 2006-08-28
Exactly what wifi card are you using. I have a linksys wusb54gc usb wifi adapter. If I use any graphical interfaces to configure it it freezes the computer. However working directly from the terminal no freeze. 
assuming your wifi card is eth1.

to scan 
```
sudo iwlist eth1 scan
```
to associate
```
sudo iwconfig eth1 essid ***
```
to get an ip
```
sudo dhclient eth1
```

---

### Post by superD on 2006-08-28
Seems useful to know. There a way to set the WEP key with that?

---

### Post by insyzygy on 2006-08-28
You can do anything the graphical tools can do and more via the console, the graphical tools are just graphical interfaces to iwconfig.

```
 man iwconfig 
```
will give all the details.

For example to set the WEP key you would type

```
sudo iwconfig eth1 key <wep hex code> 
```

Also interesting and useful is iwpriv which gives control to card specific
functions. To see what commands are available look at
```
 iwpriv eth1 
```
It might not have anything useful but on for example orinoco cards there is a card reset function that is useful if your card locks up for some reason.

To execute a command do
```
sudo iwpriv eth1 <command> 
``` 
For many cards iwpriv doesn't have anything useful.

---

### Post by dave martin on 2006-08-29
I still must be missing something I do all of the code but nothing happens.
I put in, sudo iwlist rausb0 scan
hit enter,
then, sudo iwlist rausb0 essid WANADOO-1234
hit enter,
then,sudo iwlist rausb0 key 0123456789ABCDEF etc
hit enter
then,sudo dhclient rausb0
hit enter, then nothing!

Scream, shout, try again, nope I must be doing it all wrong.

Dave

---

### Post by insyzygy on 2006-08-29
You only use iwlist to scan and set parameters of your wifi adpater, iwconfig to control access points and encryption. Also if using encryption it sometimes is necessary to set the key before the ssid

 Based on what you did below you should instead try

```
sudo iwlist rausb0 scan 
```

```
sudo iwconfig rausb0 key 01234....... 
```

```
sudo iwconfig rausb0 essid WANADOO-1234 
```

```
sudo dhclient rausb0
```


Incidentally I have a similar device  with the same chipsert, WUSB54GC.There is an issue with the driver and the thing that makes the computer freeze is the command
```
sudo ifconfig rausb0 down
``` (dont type that)
I think the graphical tools automatically cycle the device by bringing it down and then up, working at the command line you avoid that.

Also instead of sudo iwconfig rausb0 key <key> you could try 
sudo iwconfig rausb0 enc <key> they should be exactly the same though.

---

### Post by dave martin on 2006-08-30
Hi thanks for that,it seems to do what its supposed to do but I still don't get a connection.
When I do the scan it shows two networks so I think the device is working it also shows in device manager.
I've noticed the green light on the device isn't flashing which it normally does when trying to connect on other pcs.
Now I didn't install any drivers for it seeing as its seeing the networks I thought it was all ok.

Also I have this distro installed on a laptop and the same thing happens on that with this device, also it doesn't detect its own inbuilt card.

Thanks all anyway.
Dave.](*,)

---

### Post by insyzygy on 2006-08-30
Hmm. What is the exact model of your wifi adapter. 

An obvious thing to try is to first connect without encryption and make sure you are right next to the access point.
omit the encryption key line or do 
```
sudo iwconfig eth1 key off 
```

One thing I noticed with the WUSB adapters is that if you try to set the essid and its out of range it just won't change. After you set the essid run
```
iwconfig 
``` and make sure the essid is changed to what you want. If not your out of range or somethign is keeping it from authenticating.

After you did ```
sudo dhclient 
``` did you obtain an ip address or did it just say no working leases/

---

### Post by pihbar on 2006-08-30
if you are using a realtek card that is on rt2xoo or rt2500 modules, they are known to have issues with more recent kernels. some driver versions, anyway. as of 2.6.17 you cant even compile the module from source (on my arch linux system, anyway)

---

### Post by dave martin on 2006-09-02
> **insyzygy said:**
> Hmm. What is the exact model of your wifi adapter. 

An obvious thing to try is to first connect without encryption and make sure you are right next to the access point.
omit the encryption key line or do 
```
sudo iwconfig eth1 key off 
```

One thing I noticed with the WUSB adapters is that if you try to set the essid and its out of range it just won't change. After you set the essid run
```
iwconfig 
``` and make sure the essid is changed to what you want. If not your out of range or somethign is keeping it from authenticating.

After you did ```
sudo dhclient 
``` did you obtain an ip address or did it just say no working leases/
[COLOR="Red"]Did all of the above and turned off the encryption, success it connected.
Went back and put the encryption back on, entered key, nothing.
Put it all back as it was and it didn't connect, damn.
It obviously works it just can't make its mind up as to when!
When I have more time I'll play some more.
Thanks for all the advice!

Dave. [/COLOR]

---

### Post by blackest_knight on 2006-09-11
check this thread 
[http://ubuntuforums.org/showthread.php?p=1488461](http://ubuntuforums.org/showthread.php?p=1488461)

---

