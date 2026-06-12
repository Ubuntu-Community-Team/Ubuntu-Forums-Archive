---
title: "The internal 3g modem never uses turbo-3g... (HSDPA) - only UMTS"
date: 2008-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by motin on 2008-07-21
I've got a Dell XPS M1330 with the "Dell Wireless 5520 built-in 3G/HSDPA with SIM" PCI Mini Express card...

This is the way I initiate it:
sudo rmmod usbserial
sudo modprobe usbserial vendor=0x413c product=0x8138

Running UMTSMon afterwards makes for easy connections to the 3g network. However, I NEVER see any HSDPA connectivity going on, and my download rate is never higher than around 60 kb/s...

Now I verified with Dell before buying that this modem is HSDPA-compatible (up to 7.2mbps), and using the same SIM card with my old E220 on the old laptop I always got around 300 kb/s in download rates...

Does anybody recognize this and have a solution to get HSDPA connectivity on the XPS M1330?

Thanks for all advice!

EDIT:
The solution for me was to use the airprime module instead of usbserial. An How-to to do this is found here: [http://ubuntuforums.org/showthread.php?p=5449120](http://ubuntuforums.org/showthread.php?p=5449120)

However, [airprime is becoming deprecated]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246955") (in Intrepid+1...), so there should be a more universal way of achieving this. Anyways, I am happy with my current 358 kb/s and will be using airprime until it is removed next year :)

---

### Post by atlas95 on 2008-07-22
With what program do you use it after please?

---

### Post by motin on 2008-07-22
> **atlas95 said:**
> With what program do you use it after please?

Hi, I am not sure I understood your question. I use the modem in conjunction with UMTSMon in order to connect to the internet - thus the programs accessing the net are the ones used? Firefox, Transmission, apt-get etc

---

### Post by atlas95 on 2008-07-22
Sorry for my english, What program do you use for etablish the connection? wvdial? networkmanager?
I can't help you for the moment but i search because i want to buy the same card for my m1330, for the moment I use a icon225 with Hsoconnect and this work very very very well, high speed in france! but i would like an internal card.
Maybe we can use another better card in m1330? Do you have an idea?

---

### Post by motin on 2008-07-22
> **atlas95 said:**
> Sorry for my english, What program do you use for etablish the connection? wvdial? networkmanager?
I can't help you for the moment but i search because i want to buy the same card for my m1330, for the moment I use a icon225 with Hsoconnect and this work very very very well, high speed in france! but i would like an internal card.
Maybe we can use another better card in m1330? Do you have an idea?

I use UMTSMon: [http://umtsmon.sourceforge.net/](http://umtsmon.sourceforge.net/)

Although the same speeds are experienced when using wvdial...

I haven't tried Hsoconnect and not have I got a working connection yet with NetworkManager 0.7. Might as well [try]("http://www.pharscape.org/content/view/66/53/") these as well... I'll get back.

Regarding the card choice: it can, according to Dell support, connect to HSDPA networks, and it seems like a great integrated card in general - Dell's preferred choice... - I would know where to begin choosing another card for use in the XPS M1330.

---

### Post by motin on 2008-07-22
hsoconnect doesn't seem right:
> A GUI for Option 3G (HSDPA/HSUPA) devices.
A customisable Connection Manager or Dashboard for Option 3G modems. Only for Option devices using the HSO driver module - e.g. ICON225 ICON 401, GE301/2, GT301/2, GTM380 (and GE201/2, GT201/2 with fw upgrade to HSDPA 7.2 compatibility). It allows you to connect to the Internet, configure and control the device. It requires hsolinkcontrol from the hsolink package. 

I don't think this internal card uses the HSO driver module...

Also, in the current ppa version of Network Manager 0.7, I can only choose between "All", "GPRS" or "GSM" for network connectivity options. Hopefully "All" also enables 3G and HSDPA but I doubt it... trying out...

EDIT: Nah, I configured a Mobile Broadband connection, but it doesn't show up as a choice in the nm-applet network selector. 

Anyone that got the XPS M1330 3g-connected with download rates at around 300 kb/s?

---

### Post by scorp123 on 2008-07-22
> **motin said:**
>  However, I NEVER see any HSDPA connectivity going on, and my download rate is never higher than around 60 kb/s... And you are sure your area is covered with HSDPA? Because if it isn't then the modem will fall back to lower speeds (HSDPA > UMTS > EDGE > GPRS ...) ... and that's normal.

One thing you should check is with your GSM provider: Are you 100% sure your area is covered with HSDPA? And did you ever try it outside (e.g. on the balcony?) with no wall between you and the next antenna?

Also ... many providers use bandwidth shaping so a single user can't eat away all the available bandwidth. This too could play a role.

---

### Post by motin on 2008-07-22
> **scorp123 said:**
> And you are sure your area is covered with HSDPA? Because if it isn't then the modem will fall back to lower speeds (HSDPA > UMTS > EDGE > GPRS ...) ... and that's normal.

One thing you should check is with your GSM provider: Are you 100% sure your area is covered with HSDPA? And did you ever try it outside (e.g. on the balcony?) with no wall between you and the next antenna?

Also ... many providers use bandwidth shaping so a single user can't eat away all the available bandwidth. This too could play a role.

Yeah, I am pretty sure, as before the XPS M1330, I was using a E220 external usb modem with the same SIM card / operator / subscription at the same places that I am using the XPS M1330 (my flat, folks, friends) - and back then I had HSDPA connectivity practically everywhere. I did however use the Vodafone Mobile Connect Card driver GUI (which doesn't yet support Dell's internal 3g card). However, back then I could also use plain old wvdial and still get HSDPA connectivity, something I won't get when using wvdial today...

I will double-check with my operator (Tre/Three) though - having trying to reach their support now and then in several weeks and nothing but around 20min waiting queue though...

Do you know the AT commands to tell the modem to only use HSDPA (if possible)?

---

### Post by motin on 2008-07-22
Just checked with my provider and the subscription is at 7.2 mbps tops and does not include any bandwidth control... 

Next, I'll move my SIM card back to the newly firmware-upgraded E220 external usb modem (got back yesterday from service), and check if the speeds still are as low at the places where I am certain there is HSDPA connectivity.

If so, I'll know it's something with either the Dell 3g card firmware or that usbserial doesn't support HSDPA connectivity with it. (I am using usbserial instead of airprime currently since usbserial worked great with E220)

---

### Post by scorp123 on 2008-07-22
> **motin said:**
>  However, back then I could also use plain old wvdial and still get HSDPA connectivity, something I won't get when using wvdial today... Hmmm, maybe the "init" string for the modem to get the connection going is a different one? For some modems and mobile phones it's ***99#** whereas others use ***99***1#** ....

Other than that I'd recommend this thread here ... it's a bit long but in there we discuss several modems (Novatel MC950D, Huawei E220) and how to get them going ... maybe it could help you to figure out the right parameters for your internal 3G modem so it would work again with "wvdial"?

[http://ubuntuforums.org/showthread.php?t=609534](http://ubuntuforums.org/showthread.php?t=609534)

As for "AT" commands ... I'd recommend to use a tool such as **minicom** and then have a little talk with the modem to find out a few things. 

```
AT+CPIN?
``` ... asks the modem whether the entry of a PIN is required or not.

```
AT+CPIN="1234"
``` ... enter "1234" as PIN code and unlock the modem.

```
AT+CSQ
``` ... will spit out the connection quality in numbers. Possible answer, e.g. ```
+CSQ: 20,99
``` Only the first number is relevant. Numbers below 10 mean "bad signal strength", anything else between 11 ... 32 is OK.

```
AT+COPS?
``` ... should spit out the network operator your modem has connected to. Just to make sure you really are in the right network.

```
AT+COPS=?
``` ... should spit out a list of all detected network operators in your area.

---

### Post by motin on 2008-07-24
> **scorp123 said:**
> Hmmm, maybe the "init" string for the modem to get the connection going is a different one? For some modems and mobile phones it's ***99#** whereas others use ***99***1#** ....

Other than that I'd recommend this thread here ... it's a bit long but in there we discuss several modems (Novatel MC950D, Huawei E220) and how to get them going ... maybe it could help you to figure out the right parameters for your internal 3G modem so it would work again with "wvdial"?

[http://ubuntuforums.org/showthread.php?t=609534](http://ubuntuforums.org/showthread.php?t=609534)


Well, I don't know, but I don't think the init string is the problem, since establishing a connection with my 3g-provider does work great both with wvdial and umtsmon. It's but the speed that never reaches more than 60 kb/s... Or does init strings also set the network (3G/HSDPA preferred) options?

After founding the following quote (from [http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html):](http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html):)
> Many instructions on the Internet that detail how to use these modems in Linux talk about using the usbserial driver, often having to pass custom vendor and device IDs to the driver so that it recognizes the device. While this does work, the usbserial driver was not made to handle high-speed devices like EVDO and HSPDA modems. It has some small I/O buffers, and with these small buffers you will not be able to get transfer speeds greater than 60 KB/sec. There are patches available to increase usbserial&#8217;s buffer size, but with the airprime driver, this is not needed.

The Linux airprime driver can operate these modems at full-speed, after support for larger buffers was added in 2.6.18. 
... I am enticed to believe that I should have a go with configuring the airprime module next... Currently I've got it compiled but not configured: [http://ubuntuforums.org/showthread.php?p=5449120#post5449120](http://ubuntuforums.org/showthread.php?p=5449120#post5449120)

> **scorp123 said:**
> As for "AT" commands ... I'd recommend to use a tool such as **minicom** and then have a little talk with the modem to find out a few things. 

```
AT+CPIN?
``` ... asks the modem whether the entry of a PIN is required or not.

```
AT+CPIN="1234"
``` ... enter "1234" as PIN code and unlock the modem.

```
AT+CSQ
``` ... will spit out the connection quality in numbers. Possible answer, e.g. ```
+CSQ: 20,99
``` Only the first number is relevant. Numbers below 10 mean "bad signal strength", anything else between 11 ... 32 is OK.

```
AT+COPS?
``` ... should spit out the network operator your modem has connected to. Just to make sure you really are in the right network.

```
AT+COPS=?
``` ... should spit out a list of all detected network operators in your area.

Interesting :) However whenever I start minicom all letters I write end up in the terminal that I launched minicom from... Killing minicom from another terminal shows this phenomena... Simply: Minicom doesn't intercept any of the commands. Have you experienced this?

Also - do you know the AT commands to check HSDPA signal strength? Or/and how to choose "Only connect to HSDPA" for testing?
Thanks!

---

### Post by motin on 2008-07-24
Updates:
1. Configured and now using airprime driver (configuring was just "sudo modprobe airprime") instead of usbserial
2. Upgraded system BIOS to the latest (A12) - for sure...
3. Moved my SIM card to an external E220 on the same laptop + location: With the external modem I got speeds around 2.5mbit/s!

Still, when using the internal version, I always get around 0.5mbit/s despite the above...

I am running out of ideas. I have the latest wwan-card firmware from Dell as well... 

Anyone have any advice?

---

### Post by motin on 2008-07-26
> **motin said:**
> Updates:
1. Configured and now using airprime driver (configuring was just "sudo modprobe airprime") instead of usbserial
2. Upgraded system BIOS to the latest (A12) - for sure...
3. Moved my SIM card to an external E220 on the same laptop + location: With the external modem I got speeds around 2.5mbit/s!

Still, when using the internal version, I always get around 0.5mbit/s despite the above...

I am running out of ideas. I have the latest wwan-card firmware from Dell as well... 

Anyone have any advice?

AHA! Today I got up and lazily started a speed check in a firefox tab, then went on and did other things. Returning back after a while, the results showed 2.87mbit/s! I re-did the test - and got the same! So after all, this is solved, and it is due to the use of airprime instead of usbserial...

I wish that the airprime module would have recognized my card from the beginning and I would have saved lots and lots of time... I'll make an attempt to get more devices supported in Intrepid.

Thanks all with suggestions and tips in this thread!

---

### Post by scorp123 on 2008-07-26
> **motin said:**
>  solved, and it is due to the use of airprime instead of usbserial...  Glad you were able to solve this. ... But: what's the deal with this "airprime" module? I read something about the "usbserial" module being 'limited' or something like that ....  Can you please elaborate that a little?

---

### Post by scorp123 on 2008-07-29
I tried your method with the "airprime" module ... and I get no difference. The "airprime" module still loads the "usbserial" module ... and vice versa. So at least on my laptop any "effect" would be purely psychological in nature ;) ...

---

### Post by motin on 2008-08-10
> **scorp123 said:**
> I tried your method with the "airprime" module ... and I get no difference. The "airprime" module still loads the "usbserial" module ... and vice versa. So at least on my laptop any "effect" would be purely psychological in nature ;) ...

Thing is that usbserial is not capable of handling HSDPA data throughput. airprime will handle this, however airprime is getting deprecated: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246955](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246955)

Use "option" instead, as advised in the bug report. 

I use option now, and my device was already supported. I should have just "modprobe option" in the first place and I would have skipped a _lot_ of hassle :P

---

