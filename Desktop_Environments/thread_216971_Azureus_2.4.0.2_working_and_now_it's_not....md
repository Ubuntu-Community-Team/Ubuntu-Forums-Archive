---
title: "Azureus 2.4.0.2 working and now it's not..."
date: 2006-07-16
forum: Desktop Environments
---

### Post by tocnon on 2006-07-16
I'm having a frustrating problem with Azureus 2.4.0.2 and Ubuntu 6.06...

I installed Sun Java 1.5 from the repositories, then installed Azureus 2.4.0.2, also from repositories.  I was able to start up Azurues just fine and configure it.  Everything was working fine for a while and was able to download torrents, shutdown the Azureus, reopen Azureus... no problems at all.  Now, not 24 hours later, Azureus won't open-- no error message, it just won't open.  When I attempt to start it from the command line so I can see the startup messages, this is what I get...

```
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/home/username/bin/azureus/Azureus2.jar:/home/username/bin/azureus/swt.jar" -Djava.library.path="/home/username/bin/azureus" -Dazureus.install.path="/home/username/bin/azureus" org.gudy.azureus2.ui.swt.Main ''
StartSocket: passing startup args to already-running Azureus java process listening on [127.0.0.1: 6880]
```

It would seem that another java process was already started, but there are no other processes running, just the single java process started above.  No GUI ever pops up, no splash screen or anything.

Any ideas?  ](*,)

---

### Post by taurus on 2006-07-16
Do you happen to upgrade your kernel???

---

### Post by tocnon on 2006-07-16
Yes I did, actually... I upgraded to the 686 kernel after Azureus was working.  The 686 kernel seems to be more CPU intensive as confirmed by some other posts, so I boot into the original 386 kernel again now, but the 686 kernel is still installed.

---

### Post by taurus on 2006-07-16
If you don't want to use i686 kernel, then just remove it with synaptic!  Once you installed, it will be on your system and if you boot it using the i386, then your i686 will just sit on your machine, taking up space!!!

---

### Post by tocnon on 2006-07-16
As I mentioned, I'm booted into the original 386 kernel now.  I went ahead and uninstalled the 686 kernel with Synaptic, rebooted (686 no longer in grub menu), booted back into 386 kernel again, and Azureus still does not load.  So what did the kernel have to do with Azureus?

---

### Post by tocnon on 2006-07-16
here's some more information on the situation... hopefully this narrows it down if anyone can shed some light on this...

I've completely reinstalled Dapper to see where the problem is coming in that's preventing Azureus from running.  Here are the steps I followed and the outcome:

1) booted to Dapper install CD and installed as usual... rebooted
2) after initial login, I allowed the 130 auto-updates to complete, rebooted.
3) logged back in, installed the following through Synaptic:
   * Sun Java 1.5 JRE, with plugin for Firefox
   * Azureus 2.4.0.2
   * network-manager (for WPA wireless)
   * ---> removed GIJ
4) configured network-managaer for WPA wireless and connected to net fine.
5) attempted to start Azureus... GUI does not appear, but new java process is running with 0% processor usage.
6) after about 4-5 minutes, Azureus starts up, but includes a warning that another app is listening on 127.0.0.1:6880 and that command-line torrents will not work until this is resolved.

I checked the system using "lsof -i" and see no other apps listening on port 6880 and still only the single java process for Azureus running.  I have no idea what's going on here, but there has to be something inherently wrong with one or more of these initial packages.

Any help would be greatly appreciated!!

---

### Post by tocnon on 2006-07-16
the problem turned out to be related to the installation of the network-manager util.  The "lo" interface was being shutdown without having the local 127.0.0.1 address assigned, therefore java could not open a listen port on this interface for 6880.  I was able to fix the problem by reenabling the "lo" interface with these commands.  I'll simply adjust the config for network-manager to make permanent:

/sbin/ifconfig lo 127.0.0.1
/sbin/route add -net 127.0.0.0 netmask 255.0.0.0 lo

---

