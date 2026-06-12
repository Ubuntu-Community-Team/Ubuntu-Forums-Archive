---
title: "Freezes when ordered to shutdown / reboot"
date: 2009-04-27
forum: General Help
---

### Post by the_fury on 2009-04-27
Just to clarify, I'm using Ubuntu 9.04 Jaunty, with all the latest updates.

The only real flaw I've found yet is that when I order the computer to shut down or reboot, it will go through all the motions, but will stop at a blinking cursor. 

I press Alt+F7, and see that it is executing all the normal shutdown commands, except for the command "Killing all processes" is followed by [fail] and "Unmounting all filesystems" is appended with "Mount / is busy".

So.... is there any way to fix this? I am forced to force shut down, and that's not healthy for it... it also does a mandatory drive check which wastes a lot of time...

Has anyone had any success fixing this problem?

Thanks,
the_fury

---

### Post by cfurlin on 2009-04-28
> **the_fury said:**
> Just to clarify, I'm using Ubuntu 9.04 Jaunty, with all the latest updates.

The only real flaw I've found yet is that when I order the computer to shut down or reboot, it will go through all the motions, but will stop at a blinking cursor. 

I press Alt+F7, and see that it is executing all the normal shutdown commands, except for the command "Killing all processes" is followed by [fail] and "Unmounting all filesystems" is appended with "Mount / is busy".

So.... is there any way to fix this? I am forced to force shut down, and that's not healthy for it... it also does a mandatory drive check which wastes a lot of time...

Has anyone had any success fixing this problem?

Thanks,
the_fury

I had the same issue. My temporary fix? Disable wireless before shutdown/reboot. For some reason wireless is causing the hang for me.

Right-click the signal strength icon in the sys tray. Then uncheck 'Enable Wireless'. Hopefully it works for you also. Wireless re-enables itself after logging back in.

---

### Post by Keithhed on 2009-04-28
I have also been experiencing the same isse :( will try the wireless disable.  hope that works, because Intrepid worked flawlessly for me and I was expecting 9.04 to be the same.

---

### Post by iponeverything on 2009-04-28
you could automate the shutdown of your wireless like so --

put:

```
ifconfig <your wireless interface> down
rmmod <your wireless module> 

```

in your:

```
/etc/rc0.d
```

---

### Post by l-x-l on 2009-04-28
> **iponeverything said:**
> you could automate the shutdown of your wireless like so --

put:

```
ifconfig <your wireless interface> down
rmmod <your wireless module> 

```

in your:

```
/etc/rc0.d
```

I'm a noob here. I know what my wireless module is but how can I find out what my "wireless interface is"? Here's my output for lshw:

```

 *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:19:f3:79
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.10.101 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```

---

### Post by the_fury on 2009-05-05
> **l-x-l said:**
> I'm a noob here. I know what my wireless module is but how can I find out what my "wireless interface is"? Here's my output for lshw:

```

 *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:19:f3:79
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.10.101 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```


Your wireless interface is usually wlan0... unless you have multiple, which i doubt.

---

### Post by the_fury on 2009-05-05
> **iponeverything said:**
> you could automate the shutdown of your wireless like so --

put:

```
ifconfig <your wireless interface> down
rmmod <your wireless module> 

```

in your:

```
/etc/rc0.d
```

How does one insert that? How do I write a script? Sorry, I'm kind of new... I've been trying to learn for a while.

---

### Post by the_fury on 2009-05-09
Oh yes, and I'd like to point out that the above suggestion works... just in case anyone was looking for confirmation... turn off your wireless before you shutdown and it won't crash. 

But it still gives me a lot of lip before it shuts down.

---

### Post by DimGothic on 2009-05-24
Hello.

It worked for me too, but i'm still doing it manually and i can't figure out how to put the code iponeverything said.

---

### Post by the_fury on 2009-06-02
Hmm.. anyone have a permanent fix?

---

### Post by BryanFRitt on 2009-06-05
> **iponeverything said:**
> you could automate the shutdown of your wireless like so --

put:

```
ifconfig <your wireless interface> down
rmmod <your wireless module> 

```

in your:

```
/etc/rc0.d
```



How can I find out what goes in the **<your wireless interface>** and **<your wireless module>**?


p.s.
I don't know if doing this really help my "mount: / is busy", etc... problem, but I thought I'd try.
[http://ubuntuforums.org/showthread.php?t=1177702](http://ubuntuforums.org/showthread.php?t=1177702)

---

