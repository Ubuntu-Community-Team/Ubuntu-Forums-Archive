---
title: "[SOLVED] Dell Demention2400"
date: 2008-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by imjscn on 2008-06-22
Currently, I have Windows XP Professional SP3 installed, I want to add Linux to make a dual OS.
Online test recommends Ubuntu to me. I read Ubuntu system reqirement is: "64-Bit PC and Intel based Mac architectures" , I'm not sure if I meet this requirement. 

My PC is Dimension 2400 desktop, X86, Intel Celeron 2.4GHz
Total RAM is 512.00 MB
System infomation shows currently usable RAM is 199.12 MB.
Total storage is 80G, 2 partition on one harddisk.

Do I meet the Ubuntu System Requirement? If I do, among the Ubuntu family, which one is a better choice for me...considering my PC is a bit old, I need a OS which cost CPU as less as possible. 

Thanks for helping!

---

### Post by empty_tank on 2008-06-22
try xubuntu. it requires few resources.

---

### Post by imjscn on 2008-06-22
Thanks, empty-tank!
I just find out my PC is 32 bit, can I still install any of ubuntu?

---

### Post by prinknash on 2008-06-22
> **imjscn said:**
> Thanks, empty-tank!
I just find out my PC is 32 bit, can I still install any of ubuntu?

Yes. Just make sure you download the standard personal computer version (which is the default) rather than the 64 bit version.

p

---

### Post by imjscn on 2008-06-22
That's great! Thanks very much!

---

### Post by mamcgrath on 2008-06-22
> **imjscn said:**
> 

Do I meet the Ubuntu System Requirement? If I do, among the Ubuntu family, which one is a better choice for me...considering my PC is a bit old, I need a OS which cost CPU as less as possible. 


I have been running Ubuntu on a Dimension 2400 for over a year without any trouble. I did upgrade my memory to 1024MB however. I tried Xubuntu for a while but didn't really take to it. If you are unsure of which version to get, look for the following files. I would give you direct links but I don't know where you live, and which mirror would be the best for you.

ubuntu-8.04-desktop-i386.iso
xubuntu-8.04-desktop-i386.iso

P.S. These are for the live CDs.

---

### Post by imjscn on 2008-06-22
Thanks,mamcgrath! I googled out the software you listed above, downloading now:-)
nice knowing Dimension2400 works fine with Linux, I'm going to have some fun:-)
Thanks!

---

### Post by imjscn on 2008-06-24
Still have another question... normally I need to install Dell's drivers after install WindowsXP. Now, after install Xubuntu, do I still need to instll those Dell drivers?
Thanks!

---

### Post by mamcgrath on 2008-06-25
No. Everything should work fine. The Dell drivers wouldn't be any good anyway as they are Windows drivers. Over the years I have installed several versions of Ubuntu and never had any trouble with drivers, except for a wireless card some time ago. The Dimension 2400 doesn't have a wireless card anyway so no worries. 
I will keep an eye on this thread for a while and if you have any 2400 related questions I will try to help you out.

---

### Post by imjscn on 2008-06-26
Hi mamcgrath,
I installed Xubuntu (full install, not dual booting) yesterday. Everything works wonderfully and faster than install WinXP. I'm impressed by the new look and all the handy tools and the art of desktop. But I can't connect to internet.

I followed the ADSL(pppoe) instruction. It finds there's one ethernet, and I clicked "yes" to all the question, finally "pon",in the termeinal, it says something loaded, but nothing happend. Reboot didn't help. I tried to setup in Network Manager, it didn't work either, and I guess the network manager is not for ADSL.

My PC is a singal PC at home, ADSL broadband connection(there's a modern between PC and phone), use a username and password to get online. I didn't change any hardware except plug in another RAM. 

I'm now installed back WinXP because can't work out any solution without intenet. It's so nice coming back and see you'll be still around. Please help me sort out this problem, I can't live with windoz after seeing this cool Xubuntu. Many thanks!

---

### Post by mamcgrath on 2008-06-26
Hi,

I don't actually run Xubuntu but I will boot from a Live CD later and see what happens. I am surprised you had a problem with ethernet connection. Network manager will handle wired ethernet connection no problem btw. 
As for "pppoe" and "pon", I've never used these instructions? "ifconfig" is the usual command line tool for managing network interfaces. I think network manager should be the easier option for you though. 
Was your computer connected to your DSL router when you did the installation or did you connect it afterwards??
Anyway, I'll get back to you later when I've looked a bit closer at Xubuntu.

---

### Post by imjscn on 2008-06-26
mamcgrath, thanks!!! hope it won't consume too much time of yours. 

I don't understand router(I'm a PC dummy). there's a modern, it's always connects PC and phone, when reboot PC, the connection off, after reboot, need to click "connect"(in Windows) to get online. When install, it was off line because of reboot. Actually, I didn't know there is a way to connect without Operating System on. 

I tried Network Manager, choose pppoe, input username/password for the ADSL provider. it didn't work. what type do you choose in Network Manager?

---

### Post by mamcgrath on 2008-06-26
Hi again,

Don't worry about consuming my time. It's been raining here all day as usual so nothing else to do.
I have just booted from Xubuntu Live CD and was online immediately. Didn't have to do anything. What concerns me is that you always had to click on a 'Connect' button in Windows. This would suggest that all your settings were managed by an application that you no longer have in Xubuntu. 
Also, it is my understanding that PPP is for dial up access. You say you have DSL? The reason I don't have to enter settings each time is because they are already set up on my router. In this part of the world (are you in USA?) the ISP provides you with a multi purpose device which serves as a router, switch, wifi router and DSL modem. When I say router I am referring to this device. I am not sure if this is the same where you are? 
If you could give me the name and model number of your modem I might be able to help more. It is usually possible to access these from a web browser and put your username and password in there. You could try opening a browser - from Windows if you want - and typing 192.168.1.1 or 192.168.0.1 into the address bar and see what happens. These are the usual IP addresses for gateways.

---

### Post by imjscn on 2008-06-26
mamcgrath, it's raining here too, Beijing, China. We have a very little box between PC and Phone, no switch or other functions, when power on, it's working. but I have a big news to tell you---I just boot into Live CD and I got connected!!! I'm breathless!!! 
Because you said Network Manager works, so I first try the N..M.., tried statistic and automatic, it didn't work, and I left it there. Then I tried the pppoe from Terminal. Bing..go.. it connected!
I guess one reason might be... the "Automatic" is the correct setting and last time I didn't do it. 
There's still another reason for this luck which I'm fearing of... When I installed back Windoz, I installed Dell Drivers, the Broadcom is working.
What do you think?

---

### Post by mamcgrath on 2008-06-26
> **imjscn said:**
> We have a very little box between PC and Phone, no switch or other functions, when power on, it's working. but I have a big news to tell you---I just boot into Live CD and I got connected!!! I'm breathless!!!
Glad you have had some success. I am still very confused about this little black box. How does it connect to your PC? Is it by a USB cable or an ethernet cable?
> Because you said Network Manager works, so I first try the N..M.., tried statistic and automatic, it didn't work, and I left it there. Then I tried the pppoe from Terminal. Bing..go.. it connected!
I guess one reason might be... the "Automatic" is the correct setting and last time I didn't do it. 
I am not sure what you mean by 'statistic and automatic'. Can you talk me through what you did. For example - Applications --> System --> Network. What you clicked on next etc. 
> There's still another reason for this luck which I'm fearing of... When I installed back Windoz, I installed Dell Drivers, the Broadcom is working.
What do you think?
Regardless of what you installed back in Windows, once you boot from the Live CD, that filesystem is no longer accessible to you so that would have no bearing on the Broadcom working.

---

### Post by imjscn on 2008-06-26
It's ethernet cable.

I did this:
1. Network Manager/Wired/Property/choose the second in the drop down list,that's the "Automatic detect.." (can't remember the exact name), then click ok.
2. Terminal/ Sudo pppoeconf/username/passowrd/yes...yes...yes

That's all. I think, when "automatic", it can figure out what is the right IP or DNS or whatever.

I install the Broadcom Driver. If without the Driver, the Broadcom is not recongized by whatever need it in Windows. I'm relaxed a bit...as long as the driver is not needed, the problem is not big, right?

---

### Post by imjscn on 2008-06-26
If it's not the broadcom driver's problem, I'm going to re-install Xubuntu. what do you think?...let me do it, hopefully will be back with a big smile..

---

### Post by mamcgrath on 2008-06-26
> **imjscn said:**
> It's ethernet cable.

I did this:
1. Network Manager/Wired/Property/choose the second in the drop down list,that's the "Automatic detect.." (can't remember the exact name), then click ok.
2. Terminal/ Sudo pppoeconf/username/passowrd/yes...yes...yes

That's all. I think, when "automatic", it can figure out what is the right IP or DNS or whatever.

I install the Broadcom Driver. If without the Driver, the Broadcom is not recongized by whatever need it in Windows. I'm relaxed a bit...as long as the driver is not needed, the problem is not big, right?
I don't think I can help you any more. I have never had to use pppoeconf. I'm not even too sure what it does. Again I think this is because my modem has all these settings stored permanently but I don't really know. 
If you are still having problems you might try reposting a question about PPPoE in the relevant part of the forum.
Sorry I can't help anymore. Best of luck with Xubuntu. Once you get over the first few hurdles I am sure you will love it.

---

### Post by mamcgrath on 2008-06-26
[https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")

---

### Post by imjscn on 2008-06-26
mamcgrath!!!! I'm back, fresh and kicking... wish to send you a big hug from Xubuntu planet through my happy internet connection!!! It's working!!! I can't thank you enough...I stayed in internet bar the whole day yesterday reading tons of internet connection guide and solutions and fixs...mostly about using some other software to read in windows files or modify complicated code. I just didn't give the Network Manager a second thought. I think probably it's because Xubuntu set the IP or DNS address on something by defaul and it doesn't suit my provider's number, I don't know. The big thing is I'm now in a completely new planet. I'm sure..I love it...
Thank you! Hope the rain stopped on your side!

---

