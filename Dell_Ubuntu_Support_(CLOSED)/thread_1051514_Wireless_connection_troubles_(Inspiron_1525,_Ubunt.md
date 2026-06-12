---
title: "Wireless connection troubles (Inspiron 1525, Ubuntu 8.04)"
date: 2009-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tzie on 2009-01-26
I've been trying to manually connect my laptop to my wireless router. I have the ID and WEP Key for the router.

And... it does work. Sometimes. That is to say, at times I have no problems connecting. At other times, it simply refuses to connect. The only remedy I have for this is to wait, and sometimes fiddle around with the network settings. (I don't know if the latter really helps any).

Oh... and I'm a newbie to Linux. So please go easy on me?

---

### Post by no0buntu on 2009-01-27
Hey,
I am having a very similar problem.
Matter of fact, I've never been able to connect to the wireless internet and I haven't tried wired internet.
I have entered the SSID, and the WEP key, but no luck, it won't budge or anything. Even if I set it to auto-connect and restart the computer, it still won't start up the wireless internet connection.
I have a Dell Inspiron 1520 with a Dell Wireless 1390 WLAN Mini-Card.
Please help us out! :D

---

### Post by sumit.kalra999 on 2009-01-27
Hi,
i got the same kind of problem with my Dell Inspiron 1525. Mat be this problem has relation with the settings of your internet service provider proxy system. Because in my case, when the security "WEP" was disabled, network was running normal......

consult with your network manager, and get resolved it

---

### Post by Tzie on 2009-01-28
Sumit Kalra,
Sorry if this is a foolish question, but: I don't have a network manager. It's just me, the router, and the laptop. What can I do?

---

### Post by elvinatom on 2009-01-28
Similarly foolish anwer: try to disable wireless and re-enable it. Btw, I have the same laptop and there's no connection problem what-so-ever - that is until someone else goes on the wireless ... :(

---

### Post by Tzie on 2009-01-30
I've had a shot at disabling and re-enabling wireless. It doesn't seem to immediately help, though it might (I'm not sure) have a delayed reaction.

---

### Post by lmbevard on 2009-01-30
New to this forum but I just got a Dell Mini with Ubuntu. I got the Broadcom Wifi to connect to my wireless after I reset the security to WPA 64Hex instead of the stronger security that I had before.  My son and son-in-law weren't happy because their internet went down until they reset things. The only problem I still have is that eventhough I am connecting to the internet through my desktop with XP, I cannot connect to the MSHome network.

---

### Post by cptr13 on 2009-01-31
What kind of router is it?  I've had issues with cheap routers, but my linksys works like a charm.

Could that be the problem?

---

### Post by Tzie on 2009-02-01
It's one from Sky Broadband.

---

### Post by WhaleWolf on 2009-02-01
I have the same problem. I did a virus scan in my Ubuntu 8.10 OS and I found 4 viruses yesterday. Today I did another virus scan and found yet again a virus in the Firefox cache. Please check your Ubuntu OS for viruses! Maybe this is the cause of all these problems...

But my internet problem isn't solved and I am also an Ubuntu noob...

When I start up my computer I can choose out of 6 Ubuntu start-up options. 3 normal ones and 3 recovery mode ones. When I select the 3rd normal Ubuntu one my internet DOES work... (but my screen resolution is max 800x600 for some reason) but the first and second normal ones internet does NOT work. :( Screen resolution does work and can set to the confortable 1920x1200. I am using the XPS M1710 Dell computer btw.

Anyway, how can I make the internet work again in the first normal Ubuntu start-up option, when it does work in the 3rd normal Ubuntu start-up option?

I hope I am making sense here, if I don't please lemme know. :)

---

### Post by llamakc on 2009-02-01
> **WhaleWolf said:**
> **I have the same problem. I did a virus scan in my Ubuntu 8.10 OS and I found 4 viruses yesterday. Today I did another virus scan and found yet again a virus in the Firefox cache. Please check your Ubuntu OS for viruses! Maybe this is the cause of all these problems...**

But my internet problem isn't solved and I am also an Ubuntu noob...

When I start up my computer I can choose out of 6 Ubuntu start-up options. 3 normal ones and 3 recovery mode ones. When I select the 3rd normal Ubuntu one my internet DOES work... (but my screen resolution is max 800x600 for some reason) but the first and second normal ones internet does NOT work. :( Screen resolution does work and can set to the confortable 1920x1200. I am using the XPS M1710 Dell computer btw.

Anyway, how can I make the internet work again in the first normal Ubuntu start-up option, when it does work in the 3rd normal Ubuntu start-up option?

I hope I am making sense here, if I don't please lemme know. :)

How did you scan your machine, and what was found? I seriously doubt any virus would be the cause of this issue. Your mention of different kernels yielding different results are the source of the issue. 

If your machine uses restricted drivers for graphics (NVidia or ATI) perhaps you need to re-enable them for the appropriate kernel that lets wireless work?

---

### Post by ugm6hr on 2009-02-01
Viruses are not the problem.  How did you scan for viruses?

If you installed using Wubi (within Windows) - that might be causing issues.

The Dell Mini works just fine with WPA 128bit (as mine does).

The newest kernel for Intrepid 8.10 apparently does have problems with networking - there are some workarounds scattered in this forum somewhere.

There are lots of people in this thread now - for each of you - some advice:
1. Don't hijack other people's threads until they have solved their problem.
2. Start a new thread with details as suggested here: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

Hope that leads you in the right direction.

---

### Post by WhaleWolf on 2009-02-01
o_O I am sorry, I was just sharing my experience I had this weekend and trying to help, I am very new here.

I scanned my computer with the ClamAV Virus Scanner.
In the scanner I checked the boxes: 'Scan hidden', 'Thorough', 'Ignore size' and 'Save a log'. And then I scanned 'Home (recursive)'. Today I detected a virus in the Cache of Firefox (cannot give you a directory, sorry). In Firefox I cleared the Private Data including the Cache, since the file could not be quarantined or deleted in the ClamAV scanner. I did another scan with ClamAV and there was no virus this time and because of this 2nd scan I do not have a log of the virus scan where it DID scan the virus, because this program seems to save only the last scan that day. :(

Do you need any more information?

---

### Post by ugm6hr on 2009-02-01
ClamAV finds Windows viruses.  You may have had one - but it does not have any effect on Ubuntu.

---

### Post by cfischer on 2009-02-02
Not a virus ... I just did an update. I'm running Ubuntu 8.04, and all was fine on my Dell 1525 with bcm4312 using Network-Manager - simple point-and-click setup. Then I updated on Jan 30 and it installed a new kernel: from  2.6.24-22-rt to  2.6.24-23-rt and suddenly no wireless icon. No info, nothing. 

I think it has to do with the new kernel suddenly recognizing that neat little wireless switch on the right side. Can't find any clear info on how to fix.

So if I want wireless, I need to hit esc and switch to the earlier kernel.

---

### Post by Ariccanfly on 2009-02-23
On my 5125 Ubuntu 8.04.2 any kernel new than 2.6.24-19-generic freezes at work after an average 1h, when connecting to their wireless-g router)
 
Also an lscpi dosnt show and wired ethernet card at all 
and a lshw shows

 *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:32:f5:9e:eb:f3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
 
Also one out of 20 times it failes to suspent to ram, and i have to hard reset her.

This is the machine with no restricted drivers. 
I have the special dell repository installed 

0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by YWELLC on 2009-02-23
Have you tried to connect to your router via the command line, bypassing any problems with Network Manager GUI? I was having a lot of problems with NM and installed WICD (though still with some problems).  Either way, it may be helpful to determine whether or not the problem is stemming from the GUI software as opposed to your router, network card, etc.  Also, it would be easiest if you disable any encryption on the router during troubleshooting.

From the command line run:

```

iwconfig

```

There will be an entry for your wireless card.  It should look like this:

lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11 Nickname:""
Access Point: Not-Associated 

Locate your wireless device (both my Dell's this is eth1) there will be a line containing "802.11".

Then try to connect from the command line.

```

ps -aux | grep "dhclient"
sudo kill -13 <enter process id# for dhclient from above)
sudo iwconfig eth1 essid <unsecured network id here> mode managed
sudo dhclient eth1

```

And see if that connects you.

---

