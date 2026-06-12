---
title: "systemd-journald using too much memory on minecraft server"
date: 2016-12-18
forum: Gaming &amp; Leisure
---

### Post by sgian on 2016-12-18
I'm running a vanilla minecraft 1.11 server on lubuntu 16.04 for my family on LAN.  Without the minecraft server running, total memory use is about 300-400 MB.  Right now, after several hours of between 2-4 people playing, systemd-journald is at 2.2 GB for a total of 2.9GB used out of a total of 3.9 GB on the PC.  Memory use by systemd-journald keeps rising and won't drop unless the minecraft server gets rebooted.  Java, by the way, is using 25 MB.  Does anyone know what is going on with this?  

The minecraft server crashes occasionally when several people are on it moving fast, and at first I thought it was just the CPU not keeping up.  But after watching cpu fluctuate and memory use slowly rise on the Task Manager, I'm suspecting a memory leak.  Is there anything I can do to prove or disprove this theory?

Specs:
about 1.8 GHz dual core AMD Athlon cpu
4 GB RAM
NVIDIA 7xx series graphics card with proprietary driver
Oracle Java 8
Lubuntu 16.04

---

### Post by sgian on 2016-12-18
As an update, now systemd-journald alone is at 2.5 GB with no one on the minecraft server.

---

### Post by sgian on 2016-12-19
Another update, systemd-journald got up to 2.6 GB this morning after I got off the server.  So I shut it down, and the systemd-journald use seemed to disappear.  There was a total of 375 MB being used for memory by everything.  I rebooted the pc, and after reboot total memory use was just over 200 MB for everything.  I just restarted the minecraft server, and still no systemd-journald use yet.  Java is at 600 MB, Firefox at 400 MB, and total memory used is just over 1.1 GB.  So it is after someone plays on the server that systemd-journald rises, and won't drop until reboot.

---

### Post by sgian on 2016-12-19
Since the reboot, now it is java that is rising in memory and not going back down.  Java is at 1.4 GB now with no one on the server.  Does anyone know how to tell if this is a lubuntu or ubuntu issue?  I'm tempted to try opensuse lxde to see if it is an ubuntu issue because I don't know what else to try, and if the problem persists then try another desktop environment.  I'm not good enough at terminal to go without a DE.

---

### Post by mastablasta on 2016-12-20
is there any problem on the server? because RAM is there to be used. Sure it is occupied but if something else needs it it should empty and then be used by that other progam that needs it. 

lihux uses ram differently from widnows if that is what you are comparing it to. more on this topic: [SIZE=2][http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
[/SIZE]
which is why when discussing distro ram usage we would check the usage on cold boot. as after a while it will all get "used up" anyway.

also why run lubuntu on server? why not CLI only, a Light WebGUI or if you must have desktop like experience  only a Windows manager (jwm, openbox, icewm...). i mean RAM is important to you ;)

---

### Post by sgian on 2016-12-21
Thank you for responding.  And yes, the minecraft server crashed occasionally when several people were on it  moving fast, and at first I thought it was just the CPU not keeping up.   But after watching cpu fluctuate and memory use slowly rise on the Task  Manager, I'm suspecting a memory leak.  That is the only thing I could think of that would cause the crash.

I tried Ubuntu server once, but I am not good enough with terminal commands to go without a GUI, especially when I have driver issues.  I have now switched to openSUSE and went into the java control panel to limit temp files to 1G.  In openSUSE I tried different environments and none of them crashed like it was doing with Lubuntu.  Right now I am using openbox as the environment, which is comparable in memory use at startup to Lubuntu.  But Java use doesn't keep rising in openSUSE.  So I would guess it was some kind of memory control bug in Ubuntu.

My concern over RAM was that I need at least 3 GB of RAM for the server to be playable with several family members exploring at once.  The pc I am using is so old that it uses DDR2, and I was hesitant to buy more RAM for it since I could not get a clear answer with my internet searches on whether the motherboard can even handle more than 4 GB.  But I finally gave in and bought more RAM anyway for it, which should arrive tomorrow.  So I guess my concern about RAM is moot for me now since I bought more RAM and since the change in OS fixed the memory leak and resultant crashing; I'm just updating in case someone ever has a similar situation.

---

### Post by sgian on 2017-01-02
Just as an update, I tired of OpenSUSE and went back to Ubuntu 16.04 with Openbox most of the time and Unity for when I need more GUI.  I haven't seen the memory leak issue with Unity or OpenBox like there was with Lubuntu.

---

