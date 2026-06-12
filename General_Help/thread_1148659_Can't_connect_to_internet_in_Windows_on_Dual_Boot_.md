---
title: "Can't connect to internet in Windows on Dual Boot System"
date: 2009-05-04
forum: General Help
---

### Post by fatsheep on 2009-05-04
I run an XP-Ubuntu 9.04 dual-boot system.  Internet works fine in Ubuntu but on XP I can't connect.  Any ideas?

---

### Post by prem1er on 2009-05-04
Wired or Wireless?

Just a thought.  Is your network card being turned off when you boot into windows?  I have seen this happen before.

Also, are any networks being detected or can you not even see them?

---

### Post by fatsheep on 2009-05-04
> **prem1er said:**
> Wired or Wireless?

Just a thought.  Is your network card being turned off when you boot into windows?  I have seen this happen before.

Also, are any networks being detected or can you not even see them?

It's wired.  I have a network card (wired as well) but I use the LAN port on the motherboard (integrated network adapter).  I did try using the network card LAN port but it didn't work either.

---

### Post by prem1er on 2009-05-04
In Windows Control Panel > System > Hardware tab > Device manager 
Check to see if it is reporting a problem with the driver. Select your card and right click and check for changes in hardware and then update driver.

---

### Post by fatsheep on 2009-05-05
> **prem1er said:**
> In Windows Control Panel > System > Hardware tab > Device manager 
Check to see if it is reporting a problem with the driver. Select your card and right click and check for changes in hardware and then update driver.

It doesn't report any problems.  I tried to update the driver but that failed, probably because I don't have internet.  I'm going to try connecting with my network card again and see what that does.

---

### Post by fatsheep on 2009-05-06
To summarize:

I have an onboard network card (integrated into the motherboard) and a PCI network card.  I have tried using both of them in Ubuntu and XP.  On Ubuntu, they both work.  On XP, neither one works.  I have looked under the device manager as was suggested and no problems are reported with either device.  I can't upgrade the drivers as I am not connected to the internet.

I should also note I haven't been using this computer for a little while so I'm not sure if this is a new problem or not.

---

### Post by ninjapirate89 on 2009-05-06
I had this problem on my dual boot with XP. I had to boot into ubuntu and go to the manufacturer's page (Dell in my case) to download the drivers I needed. Then I saved the drivers to my flash drive and restarted into XP to install them.

---

### Post by fatsheep on 2009-05-06
> **ninjapirate89 said:**
> I had this problem on my dual boot with XP. I had to boot into ubuntu and go to the manufacturer's page (Dell in my case) to download the drivers I needed. Then I saved the drivers to my flash drive and restarted into XP to install them.

I just tried this for my PCI network card.  I went to Realtek's website, downloaded the latest driver and installed it on my Desktop but still no internet...  I couldn't find the nvidia nfornce networking controller driver on nvidia's website so I haven't tried that yet.  

Any other ideas?

---

### Post by lordbux on 2009-05-06
so no hardware error

then

it may be a problem with the internet settings in the software 
check if u have set the IP , Gateway and DNS 
in the internet settings.

right click the network icon in system tray and select properties and setting those stuff.

or just contact your ISP costomer care say that you wnat to set up the connection in windows, they can give you a step by step instruction

take care:guitar:

---

### Post by fatsheep on 2009-05-06
I'm not sure how to look at the DNS settings (although I did right click on the connection in the system tray and try to repair my connection to no avail) but this might give someone an idea:

```
C:\Documents and Settings\Fatsheep>ping www.google.com

Pinging www.l.google.com [64.233.161.104] with 32 bytes of data:

Reply from 64.233.161.104: bytes=32 time=37ms TTL=241
Reply from 64.233.161.104: bytes=32 time=37ms TTL=241
Reply from 64.233.161.104: bytes=32 time=36ms TTL=241
Reply from 64.233.161.104: bytes=32 time=39ms TTL=241

Ping statistics for 64.233.161.104:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 36ms, Maximum = 39ms, Average = 37ms

C:\Documents and Settings\Fatsheep>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.6
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

C:\Documents and Settings\Fatsheep>
```

So I am able to ping google.com (and other sites as well) but I cannot connect with either Firefox or Internet Explorer?! :confused:  I am really confused here.  I am not sure what else could be causing an issue.

---

### Post by fatsheep on 2009-05-07
I should note that this problem has been resolved.  I did not think that ZoneAlarm Firewall was running because its icon did not display in the system tray (it normally does that).  However, when I did a CTRL + ALT + DELETE and looked at what services were running, ZoneAlarm was running in the background. :o

So I turned off ZoneAlarm and the internet now works fine.  :popcorn::popcorn:

---

### Post by benon on 2009-05-08
I have the same issue. lucky u. Mine is not the firewall problem though. Don't know what it is? The hardware is fine.

---

