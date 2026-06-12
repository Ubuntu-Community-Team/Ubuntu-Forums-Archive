---
title: "Edubuntu school has network troubles"
date: 2007-04-13
forum: Education &amp; Science
---

### Post by gcmartin on 2007-04-13
We've got a school that is in ***_dire _***need of help diagnosing an issue with horrible response time: The network is as follow:
o Dual 2.2 GHz Xeons 
o 1.5GB memory
o SCSI and IDE drives
o Dual LAN cards

o Server provides DHCP and BOOtP to the LAN machines.
o all 25 LAN machines are in the same subnet
o LAN machines are using CD to boot a startup that allows them to find the server for loading.
o All student operations are on the server.
o Lan is 100Mb ethernet

The system boots and is operational serving desktops to "Diskless" LAN PC users. Response time is very fast at this point.

The PCs seem to boot up very fast to the server login screen. But when the class starts and the teacher ask the students to logon, the response time problems begin. 
All Classroom PCs are connected via one of the servers LAN cards, The other LAN card is used to route traffic for the students to the Internet.

The use of the Edubuntu server is SO BAD 
The server is running about 75% utilized when the kids are on it. When there is a classr change during each schoolday, it takes upwards of 10 minutes for the students to logon and get there Edubuntu desktop; this even before they begin class instructions. 

In summary, I need help to ID the performance issue of this LTSP scenario .

I'm suspecting that this is because the server cannot get the work out to the stations

---

### Post by tentwelveeight on 2007-04-13
I've been trying to set up an Edubuntu LTSP as well, although I'm not as far as you I can think of a few areas you mihgt check up on.

First, why are you using CDs to boot up the Thin Clients? Even without a hard drive they should boot off of the network. Perhaps they don't have PXE on the BIOS? This probably isn't the problem, but I'm just wondering.

Second, are all the students using individual accounts on the server or one single "student" account? I'm not sure if this could have any effect, but you might try setting up 25 accounts named "student1", "student2", "student3", etc. and see which one logs on fastest (if any).

Finally, (I'd guess this is your problem) you might try a gigabit NIC and router on your LAN rather than 100Mb from the server to the thin clients. You could test this by asking one class of students to only log on three or four at a time and seeing if you still have a problem. I'd guess your server is getting overwhelmed trying to log on so many students at the same time. How does it perform once everyone is in?

I'm guessing this last idea is where your problem lies because of this article:
[http://www.freesoftwaremagazine.com/articles/linux_terminal_server]("http://www.freesoftwaremagazine.com/articles/linux_terminal_server")

I've bookmarked a few other resources on edubuntu and LTSP here if you want to check it out. Good luck, please be sure to post back [here ]("http://del.icio.us/tentwelveeight/edubuntu")what the solution was when you figure it out, I'd like to avoid running into this problem when I set up my own LTSP. Cheers -joe

---

### Post by hboshoff on 2007-04-15
> **gcmartin said:**
> We've got a school that is in ***_dire _***need of help diagnosing an issue with horrible response time: The network is as follow:
o Dual 2.2 GHz Xeons 
o 1.5GB memory
o SCSI and IDE drives
o Dual LAN cards

o Server provides DHCP and BOOtP to the LAN machines.
o all 25 LAN machines are in the same subnet
o LAN machines are using CD to boot a startup that allows them to find the server for loading.
o All student operations are on the server.
o Lan is 100Mb ethernet

This seems to be the standard Edubuntu classroom server installation, although you do not mention the version. I run a similar configuration with 40 client machines using Edubuntu 6.06 LTS. My server RAM is 4 GB though.

Your hardware specs seem fine, except maybe for the network and depending on applications, the RAM. The server's ethernet card linking to the thin clients is a bottleneck, and should be Gigabit. This is useless however, unless your switch has at least one Gigabit port for the server. 100 Mb is enough for the thin clients.

I once had problems with a Gigabit ethernet chip which was not properly supported by the Linux kernel. Keep that possibility in mind.

> **gcmartin said:**
> The system boots and is operational serving desktops to "Diskless" LAN PC users. Response time is very fast at this point.

The PCs seem to boot up very fast to the server login screen. But when the class starts and the teacher ask the students to logon, the response time problems begin. 
All Classroom PCs are connected via one of the servers LAN cards, The other LAN card is used to route traffic for the students to the Internet.

The use of the Edubuntu server is SO BAD 
The server is running about 75% utilized when the kids are on it. When there is a classr change during each schoolday, it takes upwards of 10 minutes for the students to logon and get there Edubuntu desktop; this even before they begin class instructions. 

In summary, I need help to ID the performance issue of this LTSP scenario .

I'm suspecting that this is because the server cannot get the work out to the stations

Edubuntu 6.06 LTS did not install multithreading by default. If you open the System Monitor (System -> Administration -> System Monitor) you should see *four* CPU lines in the top panel of the Resources tab. This is because each hyperthread shows up as a "CPU." Because you give only one percentage (75%), I suspect you are using a quarter of your horsepower.

So if you do not see four threads, you should install symmetric multiprocessing. One way of doing this is typing the following in a terminal, while connected to the Internet:
   sudo aptitude install linux-686-smp
You can also use Synaptic Package Manager to achieve the same effect. Look in the Section Base Systems, or search on smp. In later kernels, a generic version has obsoleted separate smp.

Once you are using all the available dual Xeon processing power, use System Monitor to check the usage pattern, both of CPU and RAM. This should give you clues to the reason for slow response. Watch while students login, and when they launch applications. OOo if fairly memory hungry.

I wish you success.

---

