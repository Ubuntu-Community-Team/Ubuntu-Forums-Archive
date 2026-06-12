---
title: "My swap unmounts on me after finished booting"
date: 2012-05-04
forum: Desktop Environments
---

### Post by LordVeovis on 2012-05-04
I have Ubuntu 10.04 running on a system.  I have encrypted the setup (Luks) and have various other computer running on a similar setup.  My system keeps unmounting my swap space on me after it boots, and this is no good.  I can manually perform a swapon -a and it will show that I have 4 GB of swap again.

It seems tied into rc.local, possibly, as adding a long sleep timer in there (and nothing else) will cause swap to stay mounted until the sleep is over and the computer finishes rc.local

I would include log file entries, but I am not sure which to include.

---

### Post by cmont899 on 2012-05-04
What makes you think it is related to rc.local? Can you display the contents of /etc/rc.local and /etc/rc.sysinit if it exists?

---

### Post by LordVeovis on 2012-05-04
> **cmont899 said:**
> What makes you think it is related to rc.local? Can you display the contents of /etc/rc.local and /etc/rc.sysinit if it exists?

Well at the moment I am away from that computer.

rc.local litterally is nothing but commented out lines, the normal Ubuntu comments then:
```

sleep 300
end

```

The reason I think it is rc.local related is that without that sleep there, swap is not mounted by the time I get into X, with the sleep there, about 5 min after being in X it unmounts. If I change the time to 120 then about 2 min in it is no longer mounted...

Also it seems that when I manually mount swap later ```
sudo swapon -a 
``` it will stay mounted.

---

### Post by LordVeovis on 2012-05-04
double post, disregard.

---

### Post by cmont899 on 2012-05-04
What startup scripts run after  rc.local in runlevel 5?


ls /etc/rc5.d/


my system:
$ ls rc5.d/
README              S16fancontrol       S16virtualbox       S17loadcpufreq      S17ssh              S18cpufrequtils     S19openvpn          S21bootlogs         S22stop-bootlogd
S11nfs-common       S16rsyslog          S17anacron          S17ntp              S18atd              S18exim4            S20cron             S21libvirt-guests   
S15rpcbind          S16slim             S17dbus             S17puppet           S18avahi-daemon     S18hal              S20cups             S22rc.local         
S16binfmt-support   S16sudo             S17hddtemp          S17rsync            
S18bluetooth        S18network-manager  S20libvirt-bin      S22rmnologin

You'll see that rclocal is S22, any script that is prefix'd higher than 22 will run afterward. Other 22s would run at the same time.

---

