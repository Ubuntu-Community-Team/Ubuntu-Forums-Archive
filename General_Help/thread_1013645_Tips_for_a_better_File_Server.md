---
title: "Tips for a better File Server"
date: 2008-12-17
forum: General Help
---

### Post by rubenvazquez on 2008-12-17
Hi,
So what Im looking for is any tips on how to improve my current setup.  By improve I mean, minimize power consumption, better transfer speeds better read and write speeds, optimize networking etc....

Current Configuration.

Two 200 GB HDD in Raid 0 on different channels.  These Drives are solely for storage.

A 40 Gb drive for the OS, I'm running ubuntu 8.10.   This drive shares a channel with one of the 200 GB raid Drives.

I have all my music, movies, docuements, on the raid array and have the 40 gb just for the os.   I share the whole 400 gb via samba to rest of my network.    Its a headless server and have it set up so I can login via ssh from my macbook.

Things I want to make better....

Is my current raid setup for maximum performance?  What about redundancy with minimal disk space lost?  Is samba the way to go?   I want to use this server to backup all my other computer too.   Should I "secure" it even though its only going to be accessed locally?

Well thats all I can think of right now.  Any and all suggestions are welcomed.):P

---

### Post by jcsteele on 2008-12-17
What kind of hosts are on the rest of your network? (linux, windows, apple, etc.)

Does the server have direct internet access, or is it connected VIA a router, etc.?

Is everything wireless? wired? a mixture?


I can tell you that security should be a consideration - no matter what the setup.  You should always try to make the host as secure as possible, no matter what the circumstances - make sure to install all updates, run ufw/etc. if possible - and always keep control of who/what has access to the machine (including physical access)...

Answer these and we might be able to help better.

---

### Post by rubenvazquez on 2008-12-17
> **jcsteele said:**
> **What kind of hosts are on the rest of your network? (linux, windows, apple, etc.)**


Its a mixture.  I have a macbook.   Theres an Imac and some XP laptops floating around.

> **jcsteele said:**
> 
**Does the server have direct internet access, or is it connected VIA a router, etc.?**


Its connected to a router.  And, for now, any activity with the server  will be in the LAN

> **jcsteele said:**
> 
**Is everything wireless? wired? a mixture?**



Well the server is wired to the router.   And everything else is wireless.

---

### Post by jcsteele on 2008-12-17
Since the other hosts are windows, and if you want the most features out of your access mechanism, your stuck with samba - setup samba to share your data, etc.  Google is your friend - I am sure there are hundreds (if not thousands) of resources on all kinds of setups involving samba.  With your macbook, you might be able to use nfs, you might check on that, as I am not sure about it personally, but since apple is unix based, i don't see why it shouldn't run - again check google.

Security, keeping up with the updates is VERY important.  Running a firewall might be to your benefit as well (ufw is very easy to implement).  Since your working with windows hosts, its your call as to if you want to run some sort of antivirus software on the server - i wouldn't personally because I would expect the windows hosts to have their own antivirus, etc. (one less thing to look after as well), but its your call.

As far as tweaking, etc. its best to get everything up and running to the best of your ability and then analyze what your seeing...noone can tell you if your not getting enough network throughput until we see some sort of baseline - but the wireless will obviously be a hindrance on speed, and depending on the type of router you have and its switching/routing capabilities that might also be a bottleneck...but you also have to consider NICs, wlan adapters, etc.

Also, check in to running some kind of network stats program as well - this will simply monitor everything going across the servers nic- i recently setup darkstat ([http://dmr.ath.cx/net/darkstat/](http://dmr.ath.cx/net/darkstat/)) which was very simple on ubuntu and seemed to do the job well...

---

### Post by cb951303 on 2008-12-17
theoretically, if you use 100Mbps ethernet cards and router you should get 12.5MB/s file transfers but there is always attenuation in signal originating from long cables etc so the actual value is lower than that. Bearing these in mind, measure the file transfer rates from server to all of your machines and compare. I get 8MB/s with my samba server (both linux) with a very long cable.

---

### Post by bgerlich on 2008-12-17
1. Switch to a stable distro - like debian stable, centos or ubuntu hardy. It will save you a ton of grief, you won't have to lug your monitor or laptop to the server if network goes down or something happens during the boot sequence.

2. To minimize power usage start with a clean base system install (no Xserver!) and add functionality - no unneeded processes stealing tics.

3. Try to experiment with undervolting your processor and even disabling the fan, with some processors and a good cooling setup it's possible and will save power and reduce noise.

4. Pry out every unneeded hardware form the machine, disable internal cards and ports you don't use in BIOS.

5. Compile a custom kernel without module support and with all unneeded functionality axed.

That is all I can think of. Cheers,

---

### Post by cb951303 on 2008-12-17
> **bgerlich said:**
> 1. Switch to a stable distro - like debian stable, centos or ubuntu hardy. It will save you a ton of grief, you won't have to lug your monitor or laptop to the server if network goes down or something happens during the boot sequence.

2. To minimize power usage start with a clean base system install (no Xserver!) and add functionality - no unneeded processes stealing tics.

3. Try to experiment with undervolting your processor and even disabling the fan, with some processors and a good cooling setup it's possible and will save power and reduce noise.

4. Pry out every unneeded hardware form the machine, disable internal cards and ports you don't use in BIOS.

5. Compile a custom kernel without module support and with all unneeded functionality axed.

That is all I can think of. Cheers,

I'm pretty sure these won't effect the file transfer speed... The bottleneck is not the hardware it's samba server

---

### Post by bgerlich on 2008-12-17
> **rubenvazquez said:**
> By improve I mean, minimize power consumption, better transfer speeds better read and write speeds, optimize networking etc....

cb951303,

The bottleneck is wireless networking though an access point. No point in worrying about file transfer speeds, the highest he will be able to achieve will be about 6mb/s with normal transfer rates lower than that.

He might as well work on a quiet and efficient server, because he won't go any faster.

---

### Post by jcsteele on 2008-12-17
> **bgerlich said:**
> 
5. Compile a custom kernel without module support and with all unneeded functionality axed.

Why?  So when a problem occurs you can't properly report a bug because any developer will most likely say "try it on the stock kernel"....running a custom kernel should be reserved for people who NEED custom for whatever reason - not for a basic fileserver, nor for 99% of the people...if you work at a hosting company and your trying to squeeze the very maximum of performance because of traffic and mysql and php are killing your cpu/mem then MAYBE it might be a good idea....for this situation though I am going to have to disagree.

---

### Post by ibuclaw on 2008-12-17
If you have a multi-core CPU server, you could try out [irqbalance]("http://irqbalance.org/"), it's in the repository, so you can just apt-get install it.

And for powersaving, you can alway check out the tips and tricks they give at [lesswatts]("http://lesswatts.org/") concerning network cards and hard drives, though, truth be told, not all tips will be for your advantage in running an optimal server, so you may go out of your way to find a good compromise between "minimal power" and "full throttle" that works for you.

Regards
Iain

---

### Post by rubenvazquez on 2008-12-17
> **jcsteele said:**
>  if you want the most features out of your access mechanism, your stuck with samba.  With your macbook, you might be able to use nfs.


Would using NFS with the all the macs improve throughput?  I dont really have a problem with it now.    Would there be a conflict if I share the media using both methods at the same time (Samba for windows, NFS for mac)?

> **jcsteele said:**
> 
Security, keeping up with the updates is VERY important. 


Its a headless server.  Can i have apt-get automatically download security updates?

Also, Ive been wanting to run some sort of network throughput program to see what kind of performance i have.  Any suggestions

[QUOTE=cb951303]
theoretically, if you use 100Mbps ethernet cards and router you should get 12.5MB/s file transfers 
[/QUOTE]
I am using 100Mbps tech throughout the network.   But im only seeing about peeks of about 2MB/s seen from my macbook connecting wirelessly.  Im using istat menus.

[QUOTE=bgerlich]
1. Switch to a stable distro - like debian stable, centos or ubuntu hardy. It will save you a ton of grief, you won't have to lug your monitor or laptop to the server if network goes down or something happens during the boot sequence.
[/QUOTE]

Havent had any problems yet

[QUOTE=bgerlich]
2. To minimize power usage start with a clean base system install (no Xserver!) and add functionality - no unneeded processes stealing tics.
[/QUOTE]
I dont have gnome running

[QUOTE=bgerlich]
3. Try to experiment with undervolting your processor and even disabling the fan, with some processors and a good cooling setup it's possible and will save power and reduce noise.
[/QUOTE]

I would love to do this...How?  whenever I check top im only using 2%

[QUOTE=bgerlich]
4. Pry out every unneeded hardware form the machine, disable internal cards and ports you don't use in BIOS.
[/QUOTE]
DONE


ALSO my handy dandy kill-a-watt says im using about 64 watts at idle

---

### Post by bgerlich on 2008-12-17
2 Mb/ps (if you mean megabytes) is actually pretty decent, that is about what you would get on a ~20-30m distance. Wireless network is the bottleneck here.

I don't know what CPU you have. If your BIOS supports it you can set your CPU clock and/or multiplier. For more info on your specific setup check the overclocking (sic!) sites and forums. If you can overclock it, most probably you can underclock it.

If you are serious about power usage aware setup, use powertop to determine what services make your system greedy. Also switching to more efficient PSU will usually bring the power consumption down.

---

### Post by rubenvazquez on 2008-12-18
Ya I meant MB/s.   The server is running on an old pentium 4 1.5Ghz.   The bios is pretty limited in its features.   I would like to get rid of some process that I dont need too.   Does anyone have any suggestions on the Raid 0 setup?

---

