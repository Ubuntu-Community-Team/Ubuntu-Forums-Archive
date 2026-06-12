---
title: "Wireless drivers dell latitude D610"
date: 2006-02-19
forum: Desktop Environments
---

### Post by jbox449 on 2006-02-19
Where can I find wireless drivers for my Dell latitute D610.

It is a Dell Wireless 1470 dual band wlan mini-PCI card

---

### Post by qferret on 2006-02-19
Dell's website.

You'll need to use a Windows driver and a program called ndiswrapper.

I don't know which version of the driver to use, but I had to try a few with my D600 before I found one that worked. The first 2 were getting recognized as a bluetooth device LOL.

btw...the D600 has a 1350, but I would imagine that one flavour or another of the Windows driver for the D610 should work with ndiswrapper.

---

### Post by jbox449 on 2006-02-24
i got the driver downloaded and used the gui ndiswrapper.  it says that hardware is present but in the hardware manager it still says it does not recognize it.  and does not add eth??? in the network connections any ideas?

---

### Post by qferret on 2006-02-26
Check out the post where I got mine working:

[http://www.ubuntuforums.org/showthread.php?t=66651](http://www.ubuntuforums.org/showthread.php?t=66651)

mlomker was very helpful in pointing me in the right direction as to what to look for. Rather than re-invent the wheel, I'll send you to that thread.... ;)

Pay particular attention to what "dmesg | tail" gives, as that was the big clue on mine.....the driver I was using made ubuntu think it was a bluetooth device...

G'luck

---

### Post by Chargerbear on 2006-06-25
If you have installed Dapper Drake from the ISO CD or upgraded from Breezy Badger to Dapper Drake and you would like to use ndiswrapper for  your broadcom 43xx wireless card , you'll need to disable the bcm43xx driver by running: 

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

You can copy and paste this into your root terminal from this post. I never make typing errors when I do this. This will ensure that the bcm43xx driver doesn't load at startup and will therefore not conflict with ndiswrapper.

Reboot your computer.

The next step is to find out if you have the ndiswrapper package installed. If you upgraded from Breezy you probably do, if you installed Dapper from the CD you probably don't. Open Synaptic Package Manager and search for ndiswrapper. Install if need be. 

Then you will need the driver. I got mine from my windows installation. I got this computer from my daughter for father's day and wanted to get my WLAN going, so I didn't have my windows partition visible to Dapper yet. I did a windows search for bcmwl5.inf and copied it to a CDRW. If you don't have Windows you can Google Dell Wireless 1470 Dual Band WLAN driver. Put it in a new folder of your choice if you download it. When you unzip the EXE it makes a mess.

Now the easy part.  Open your root terminal type 
ndiswrapper -i (Driver file)

Mine looked like this:   

ndiswrapper -i /media/cdrom/bcmwl5.inf
                                    ndiswrapper -l
                                    ndiswrapper -m

Reboot your computer and your in business. When Dapper comes back up unplug your Ethernet cable and go surfing. 

I hope this gets you guys going faster then me. It took me a day and a half to figure this crap out. My other laptop was an IBM Thinkpad and the WLAN just worked. This is the first time using ndiswrapper for me. I tried to use the  43xx program first. I failed miserably with that. Ended up reinstalling Dapper.

Chargerbear

---

### Post by jivebiscuit on 2006-10-13
I got ndiswrapper to work, but only if I put the D610 in 'Standby' and then taking the D610 out of Standby. I have to do this everytime I go wireless...

---

### Post by gb5757870 on 2006-10-14
Good to see I'm not the only person scratching my head.
I followed the instructions but when running the "ndiswrapper -i bcmwl5.inf" it listed the below:
[B]Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2[/B]

Then when running ndiswrapper -l I got:
[B]"Installed ndis drivers:
bcmwl5  invalid driver!"[/B]

Help ?

---

### Post by jivebiscuit on 2006-11-11
I upgraded to Edgy 6.10, and I still have to boot up, and log in, then go to standby and come out of standby for the WiFi to work.  Anyone know whats going on there?  I mean, the wireless works fine, but I wish I didn't have to go to 'Standby' mode and back out to make the wireless work.  Any suggestions?

---

### Post by Kubunteando on 2006-12-16
Have you tried fw-cutter instead of ndiswrapper in edy?
I have a Dell Latitude D600 with a Dell Wireless 1470 rev(2) (according to the output of "lspci").
I have installed fw-cutter in edgy and I used the Windows driver from [www.dell.com](www.dell.com) for the Dell 1470. The exact version is 3.120.27.0 of bcmwl5.sys.

I can put the adapter even in mode monitor, what I cannot do with ndiswrapper.

But KNetworkManager does not connect correctly with this wireless adapter (neither when I use ndiswrapper).
Also thw wireless assistant fails to connect. So I have to set up the connection using the appropiate commands in a shell console. But this is a different problem. I have had it already with other wireless adapters.

---

