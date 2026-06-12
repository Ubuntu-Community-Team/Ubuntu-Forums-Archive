---
title: "Problems installing Speedtouch 330.."
date: 2006-08-12
forum: Desktop Environments
---

### Post by simonpearson on 2006-08-12
Hi there, this is my first post to ubuntuforums, so please be gentle!

I downloaded and Dapper (6.06lts?) this morning (was up early with a very active and very awake baby!) and proceeded to install on a spare hdd. Very impressed indeed, as it worked out of the box.

The next challenge is connecting to the 'net.

I have a Speedtouch 330 Modem, and my ISP is Tiscali (UK).

I have followed the guide[here]("http://www.ubuntuforums.org/showthread.php?t=44763"), which although was a howto for hoary, gave the same advice as a lot of the other help guides out there.

My problem is that when I plug my usb modem back in, the following log message is shown:

```
 abcxyz@incoming:~$ tail -f /var/log/messages
Aug 12 07:09:56 incoming gconfd (root-6114): GConf server is not in use, shuttin g down.
Aug 12 07:09:56 incoming gconfd (root-6114): Exiting
Aug 12 07:10:11 incoming gconfd (root-6138): starting (version 2.14.0), pid 6138  user 'root'
Aug 12 07:10:11 incoming gconfd (root-6138): Resolved address "xml:readonly:/etc /gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 12 07:10:11 incoming gconfd (root-6138): Resolved address "xml:readwrite:/ro ot/.gconf" to a writable configuration source at position 1
Aug 12 07:10:11 incoming gconfd (root-6138): Resolved address "xml:readonly:/etc /gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 12 07:10:11 incoming gconfd (root-6138): Resolved address "xml:readonly:/var /lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 12 07:10:11 incoming gconfd (root-6138): Resolved address "xml:readonly:/var /lib/gconf/defaults" to a read-only configuration source at position 4
Aug 12 07:13:40 incoming gconfd (root-6138): GConf server is not in use, shuttin g down.
Aug 12 07:13:40 incoming gconfd (root-6138): Exiting
Aug 12 07:15:41 incoming kernel: [4295775.633[CODE][CODE]
```[/CODE]000] usb 1-2: new full speed USB device using ohci_hcd and address 3
Aug 12 07:15:42 incoming kernel: [4295776.516000] usb 1-2: reset full speed USB device using ohci_hcd and address 3
Aug 12 07:15:42 incoming kernel: [4295776.668000] usbcore: registered new driver speedtch
Aug 12 07:15:42 incoming kernel: [4295776.751000] speedtch 1-2:1.0: no stage 1 firmware found![/CODE]

I'm guessing that my problem is maybe the firmware I have used (0.3012k) is out of date and doesn't work with dapper, that I am have missed something in the guide (which I have repeated after a reinstall as a double check) or maybe something else is amiss.

Any advice would be gratefully received!

Yours,
Simon

---

### Post by coffeecat on 2006-08-12
I did get the Speedtouch working with both Ubuntu and Fedora last year, but more as an exercise in seeing if it could be done. I can't help you with the specifics of the Speedtouch, but I can offer some alternative and, I think, valuable advice. Get yourself an ethernet ADSL modem/router. Connect it to your ethernet port, configure it through its web-based interface (much, much easier), and surf away.

Reasons:

- The Speedtouch is a second-rate piece of equipment designed for Windows and given out by ISPs because that makes life easier for their help lines - one piece of equipment used by the 90% of their customers using Windows.

- An adsl modem/router is intrinsically more secure with a built-in firewall and NAT.

- USB was not designed for networking and usb modems are, at best, a poor compromise. It will reduce your internet speed, especially if you have the new(ish) 8Mbs MAX service. Ethernet was designed for networking - much better.

- An adsl modem/router is far easier to set up (see above).

- If you get more/another computer(s), you just connect to the router and share the broadband connection.

I'm not necessarily talking about wireless here. Same principles apply to wired/wireless routers.

Best of luck whatever you do, and welcome to the forum. :)

**Edit:** But if you're really intent on giving yourself a headache :wink: you might find [this link]("http://www.linux-usb.org/SpeedTouch/") helpful. The Ubuntu version includes instructions for Dapper. The location for the firmware is different in Dapper - this might be your problem. HOWTOs for ealier versions of Ubuntu need modifying for Dapper.

---

### Post by simonpearson on 2006-08-12
hi coffeecat, 

Thanks for the response! You're advice hasn't gone unheeded from previous posts, and I am saving up the pennies for an adsl router (got my eye on a draytek 2700 wired) but in the mean time, I'd still like to facilitate the switch to ubuntu :)

soooo...

if anyone has come accross this issue and have resolved it, or can offer some advice, that'd be great!

Simon

 - oh just re-read your last edit.. lol! Gonna try the instructions on that link!

---

### Post by simonpearson on 2006-08-12
Ok quick update.

1) I've finally managed to connect - writting this from Ubuntu 6.06 now :)

2) The problem (i think) was where I hadn't properly created the /etc/ppp/speedtch file, and the 

3) I had "0.00" in the speedtch file, where I should be using 0.38 #(UK)

coffeecat.. thanks for the link - that worked a treat!

---

### Post by coffeecat on 2006-08-12
**Simon**, Glad it worked, and I'm glad you can connect to the internet with Ubuntu now. So much more secure than that other OS from Redmond.

I'm always a little nervous about advising people to ditch the Speedtouch and get an adsl modem/router. Why? I did this on another forum and the poster went out and bought one of the few routers whose firmware couldn't cope with IPv6 addressing (which is enabled by default in Linux, but not in Windows). I had to walk him through disabling IPv6. Then I suggested he update the router firmware and somehow he managed to completely disable the router and he had to take it back to the shop. ](*,) We got there eventually. :(

I hope this doesn't happen to you. My first router (a DLink) did this to me when I first started with Linux and it took ages to sort out, because I didn't then know anything about networking or what was wrong. Upgrading the firmware finally fixed that one. My second one (a Linksys) worked ootb, but no guarantee that all Linksys routers will. I don't want to concern you unnecessarily, but reading [this thread]("http://www.ubuntuforums.org/showthread.php?t=87798") sometime might be useful - on a just-in-case basis. :wink: Look towards the end of the thread for Dapper-specific instructions, but the whole debate is interesting.

---

### Post by simonpearson on 2006-08-14
Certainly will thoroughly investigate this before making a purchase! Again, excellant advice, thanks.

At the very least, I am a bit more knowledgable in usb based adsl modems (well speedtouch anyway) so if all else fails, I can fall back on this.

Cheers
Simon

---

### Post by Scythe!? on 2006-08-14
I have the same modem and managed to get mine to work. However, because my ISP isn't stable sometimes, it doesn't connect on boot. To connect manually type this into terminal.
```
sudo pppd call speedtch
```

---

### Post by geppetto on 2007-11-07
There are lots of howtos about this modem in the Web: you can give a look to the one I am preparing at this address

[http://docs.google.com/Doc?id=dd75t737_20cbrgmj](http://docs.google.com/Doc?id=dd75t737_20cbrgmj)

maybe it helps.

Geppetto

---

