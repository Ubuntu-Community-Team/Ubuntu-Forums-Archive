---
title: "Modem Auto dialing at boot-up"
date: 2008-12-03
forum: Desktop Environments
---

### Post by KE4AVB on 2008-12-03
Just recently got a hardware modem for my system so that I get Ubutbu 8.04 to use the internet. How do you stop it dialing out at boot-up as I don't always need to be on the internet?

I am downloading the updates for my system so problem be already fixed in one of those updates but it take a while as they are over 250megs and that will around 20 hours of downloads.

Ke4avb

---

### Post by KE4AVB on 2008-12-09
Installed all but two of the updates and my system is still auto dialing at the startup. Any ideas?

---

### Post by keithld on 2008-12-09
Did you try going to the Modem Manufacturers site and look around to see if they have any "Linux" support for the device???...

Also is it an "Internal or External Modem and what Brand is it???"... This info will help the experts and others here with trying to solve the problem...

This site addresses Dial up Modems but maybe not your specific problem... [**Debian Linux Modem Configuration **](http://www.aboutdebian.com/modems.htm)...

Here is my Google search for the Auto-Dial problem: [**modem auto dials in linux**](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=KaG&q=modem+auto+dials+in+linux&btnG=Search)...

---

### Post by KE4AVB on 2008-12-10
The is a MultiTech modem model MT5634ZPX-PCI-U/NV.
This is a hardware PCI internal modem. I using Ubuntu 8.04 LTS with two different kernels. Both kernels are doing the same thing, it doesn't which one I use. It was suggested that problem be in a configuration file but don't which one to look for as I am new to Linux (only a few weeks old).

Meanwhile I will email MultiTech technical support and see if they have any ideas. 

I am also using the modem with Windows 2000 Pro without problems other line noise which I am working on to solve. I was able to reduce it somewhat but need order a few parts complete the filter. I still receiving at 40KBPS and sending at 28.8KBPS V92 compressed.

I am finding that Linux is being more of pain to get work than I lead to believe. I still got figure why the CD Burn won't CD-RWs it erase them and then won't recognize for reburn. The drive works fine under Windows. It is an older Plexwriter 8/4/32a. I got a couple other faster drives to try.

KE4AVB

---

### Post by KE4AVB on 2008-12-11
It appears that problem definitely in Ubutbu. The following a small extract from the system log file. 

Dec 11 17:20:01 arlan-desktop chat[4135]: ATDTxxxxxxx^M^M
Dec 11 17:20:01 arlan-desktop chat[4135]: CONNECT
Dec 11 17:20:01 arlan-desktop chat[4135]:  -- got it 
Dec 11 17:20:01 arlan-desktop pppd[3957]: Serial connection established.
Dec 11 17:20:01 arlan-desktop pppd[3957]: Using interface ppp0
Dec 11 17:20:01 arlan-desktop pppd[3957]: Connect: ppp0 <--> /dev/ttyS1
Dec 11 17:20:06 arlan-desktop pppd[3957]: CHAP authentication succeeded: 
Dec 11 17:20:06 arlan-desktop pppd[3957]: CHAP authentication succeeded
Dec 11 17:20:06 arlan-desktop kernel: [  154.292208] PPP BSD Compression module registered
Dec 11 17:20:07 arlan-desktop kernel: [  154.559118] PPP Deflate Compression module registered

I x'd out the actual number being dial. Now how I fix this problem.

KE4AVB

---

### Post by KE4AVB on 2008-12-17
Okay fellow Ubuntu users. I have manage to stop my system from auto dialing at startup.

It appears that network point to point setup is for those that has a separate phone line for dialup modems and DSL users. In my case, I use my phone line for voice and dialup internet connections. Also I do not have unlimited internet connection time. There is no option listed for my type of service requirements. I would have thought that there would been an option of either Auto or Manual connections.

After several weeks of searching, reading and trial-n-error, I finally found what was happening.

First I found out from the system log that my system was running a chat script.
Second I found the point to point modem setup was adding an auto ppp0 line to the network file. This was running the ppp0 chatscript automatically.

Disabling the default internet connection box did not resolve the problem.

Disabling the auto system updates areas did not resolve.

Finally I disable the point to point modem setup which of course disabled it use through the network setup.

I am very disappointed in the lack of support on this problem. It took me nearly two of reading and searching through system files to find why this was happening.

I have worked around this problem...

KE4AVB

---

