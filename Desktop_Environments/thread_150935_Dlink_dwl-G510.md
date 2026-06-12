---
title: "Dlink dwl-G510"
date: 2006-03-27
forum: Desktop Environments
---

### Post by pacificdrums on 2006-03-27
OK I can not get my wireless card to work. I have tried everything I can think of and all it can do is see the networks. So I see them but I can not connect to them or dhcp or anything. I have used ndiswrapper and installed the driver and it says the hardware is there but it will not work. I have seen people saying they got this card to work so I know it should work. I have tried everything I know which is not a ton so any help would be appreciated.

---

### Post by Sendervictorius on 2006-03-27
What do you mean by "see the networks". It would help if you could be more specific about what stage of connection you have got to. Is the card detected? module loaded? ifconfig, iwconfig? Can you see your access point/ SSID, iwlist scanning, Can you ping your access point? 

Things that spring to mind - have have you set your firewall? Is your access point encrypted (WEP/WPA) - is the WEP/WPA setup correctly? all these will stop DHCP if you can "see" the accesspoint.
preventing DHCP converstion

---

### Post by pacificdrums on 2006-03-27
OK sorry, yes I see the SSID, my hardware is detected, I have loaded the .inf for the card, I can't ping anything but myself (the computer I am working on), it is encrypted with WEP 64bit hex, and I will post what ifconfig and stuff gives me later if you want.
I did try taking the WEP off at one point, if you think that is a good idea at first I can take it off again.
I have the wireless working on a Ubuntu laptop so I know it dose work.

If you need anything else from me let me know. Thanks again for any help.

---

### Post by Sendervictorius on 2006-03-27
Always get it working without WEP - one less thing to complicate. You can enable it later. I would recommend turning it off.

Have you checked out this guide, it has all you need to get wifi cards working: 
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

I won't be around till next weekend, so won't be able to help, unless you don't mind waiting. 

This guide has the info to troubleshoot:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

All below comes from that guide.

A starting point is to run 
sudo iwconfig
and see if you have a working driver (see above link)
If it works, then you know that ndiswrapper is working. Otherwise you need to backtrack. I would guess that you are ok, because you can see the networks.

Then do sudo ifconfig. Without a successful DHCP you wont see the second line - starting "inet addr". But it will tell you whether you have a connection to your access point.

Then do sudo iwlist <your i/face> scan - will tell you whether your PC end is ok. If this is ok, then there is nothing wrong with your ubuntu setup.

With all that eliminated, the detective work starts. You need to figure out why your access point is not talking to your pc. Could be lots of reasons. Have you used the access point in windows? Encryption issue, firewall at the pc end, security at the access point end... 

I hope thats a good start. I'll check up on Sunday, and see how you get on.

---

### Post by lowest.common.denominator on 2006-03-30
this might be the solution your looking for:

[http://www.ubuntuforums.org/showthread.php?t=145836&highlight=wifi+dlink](http://www.ubuntuforums.org/showthread.php?t=145836&highlight=wifi+dlink)

---

### Post by pacificdrums on 2006-04-05
I am having the same problem on another computer with a Dlink dwl-G120.

After I configure everything and try to connect to my network i run iwconfig and it says under essid "off/any". I am going to try to update ndiswrapper. Please help!! ](*,)

---

### Post by Sendervictorius on 2006-04-06
This link may be of help with the G120. It seems the prism54-usb package does not work, But this link shows how to set up ndiswrapper sucessfully, with a but of skulduggery. The posting even lets you download the windows dlls for installation on linux.

[http://www.linuxquestions.org/questions/showthread.php?t=214805](http://www.linuxquestions.org/questions/showthread.php?t=214805)

---

