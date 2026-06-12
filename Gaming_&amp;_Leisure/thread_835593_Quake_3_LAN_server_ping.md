---
title: "Quake 3 LAN server ping"
date: 2008-06-20
forum: Gaming &amp; Leisure
---

### Post by rroosa on 2008-06-20
Hi All,

I am still a big fan of Quake 3 Arena, and often still play this game on my LAN.

I want to use Kubuntu to run the server, but have found it to ping higher than windows. 

I have trided Kubuntu 8.04, Xubuntu 6.06LTS, and Ubuntu 6.06LTS with the same results. Average ping is about 30 compared to an average Windows ping of 2. 30 is simply too laggy for LAN gaming.

Here are the things I know:

1. I have an extensive Quake 3 Arena CVAR and tweaking knowledge. All of the tweaks I like in Windows are set the same on the Linux server.

2. No firewall is running in Linux - I use the firewall on my router only to block outside traffic. LAN traffic is unhindered. (I did have a firewall problem on an install of SuSe, but I prefer K/X/Ubuntu anyway.)

3. There is no hardware difference in the machine. This is just the Linux install vs. the Windows install.

4. System Specs are:

IBM Intellistation M
Intel Xeon 2.4Ghz HT
1GB RAMBUS
17GB SCSI HDD
ATI FireGL 8800 Videocard
CD-RW/DVD-ROM Combo drive

I know they shouldn't really make a difference with Quake 3 Dedicated server, but I thought I would include them anyway just in case.


Oh, and in Windows I am running the dedicated server using UDP. Not some crazy mod to use NETBUI or something weird like that.

If anyone has any ideas on why my pings are 15 times higher, that would be great. 


Thanks,

Rob

---

### Post by ykram on 2008-10-16
Just came across this same problem tonight when trying to setup a dedicated server. It seems as though the q3ded binary provided by ID is flawed as I had 30-31 ms on a lan server too and I agree, its way too high. I tried ioquake3's dedicated server and that worked flawless, thats to say 0-1ms :)

---

