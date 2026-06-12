---
title: "Failing to boot up"
date: 2020-02-29
forum: Desktop Environments
---

### Post by sniper8752 on 2020-02-29
I am running 16.04 Desktop, and my load times have been taking longer than normal.  I am using LUKS for hard drive encryption.  After typing in the password for my drive, it takes a while to load.  I rebooted twice, and on the third time, I just let it go, and after several minutes of waiting, it finally let me login.  
I've captured logs.  Here is some of the output from boot.log that I thought would be relevant to diagnose/troubleshoot this issue:
```
         Starting Power-Off...         Stopping Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  Volume group "ubuntu-vg" not found
  Cannot process volume group ubuntu-vg
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  Reading all physical volumes.  This may take a while...
  Found volume group "ubuntu-vg" using metadata type lvm2
  WARNING: Failed to connect to lvmetad. Falling back to device scanning.
  2 logical volume(s) in volume group "ubuntu-vg" now active
/dev/mapper/ubuntu--vg-root: recovering journal
/dev/mapper/ubuntu--vg-root: clean, 490410/31121408 files, 96696184/124455936 blocks
[^[[0;1;31mFAILED^[[0m] Failed to start Raise network interfaces.

```
Here are the other logs that I have captured: 
 [ATTACH=CONFIG]285109[/ATTACH]

---

### Post by TheFu on 2020-03-04
Looks like the network is the real issue, assuming the HDD isn't failing.  The recovering journal usually means some sort of system crash happened. Was that the case?  Was power cut?

Run **systemd-analyze blame** to see where the time is being wasted.
You can make the network come up faster by setting the parameters on the system, not using DHCP.  Sometimes the issue is actually due to a slow DHCP server on the network.

For the failing disk, check the SMART data.  Many ways to do it.  I'd use smartctl, but there are others.  Plenty of threads here about that.  [https://ubuntuforums.org/showthread.php?t=2431297&highlight=smartctl](https://ubuntuforums.org/showthread.php?t=2431297&highlight=smartctl) is one.

---

### Post by sniper8752 on 2020-03-04
I may have lost power, and it shutdown.  Also, had to do a hard reboot because it took too long to bootup. 
Is there any way to define how long a dhcp request should take? (ie, greater than 1 min, quit)?
Here are the top 6:
```
23.834s motd-news.service         12.230s apt-daily.service
          4.463s plymouth-quit-wait.service
          3.180s apt-daily-upgrade.service
          1.477s bolt.service
          1.110s fwupd.service

```

---

### Post by TheFu on 2020-03-04
Here's mine on an 18.04 box:
```
$ systemd-analyze blame
          1.795s systemd-networkd-wait-online.service
          1.065s keyboard-setup.service
           789ms cloud-init-local.service
           766ms cloud-config.service
           659ms dev-vda2.device
           518ms cloud-init.service
           391ms networkd-dispatcher.service
           390ms cloud-final.service
           221ms systemd-udev-trigger.service
           209ms systemd-journald.service
```
If you don't use automatic updates, which I do not, then you don't need any of those APT services and definitely don't need the Canonical "news/MOTD" stuff.

My systems mostly have static IPs, no DHCP.  The one above does too.

Disable the APT stuff:
```
$ sudo systemctl stop apt-daily.timer
$ sudo systemctl stop apt-daily.service
$ sudo systemctl disable apt-daily.timer
Removed /etc/systemd/system/timers.target.wants/apt-daily.timer.
$ sudo systemctl disable apt-daily.service
$ sudo systemctl mask apt-daily.timer
Created symlink /etc/systemd/system/apt-daily.timer â /dev/null.
$ sudo systemctl mask apt-daily.service
Created symlink /etc/systemd/system/apt-daily.service â /dev/null.

```

We don't have to live with Canonical's defaults.

---

### Post by sniper8752 on 2020-03-05
Wouldn't disabling automatic updates be a bad idea security-wise? 
Should I consider running a fsck as well?

---

### Post by sniper8752 on 2020-03-05
Also, tried to do the long test, and just get this:
```
sudo smartctl -t long /dev/nvme0smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-88-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


NVMe device successfully opened


Use 'smartctl -a' (or '-x') to print SMART (and more) information



```

---

### Post by TheFu on 2020-03-05
> **sniper8752 said:**
> Wouldn't disabling automatic updates be a bad idea security-wise? 
Should I consider running a fsck as well?

I've been running servers for clients over 25 yrs.  We don't allow automatic updates.  

Got burned about 10 yrs ago when an automatic update removed a DB package and installed a different one because a package maintainer never considered that someone would use a different DBMS than the one he used.  That day, we stopped allowing any automatic updates and manually update early on Saturday mornings.  We had only enabled automatic updates for about a year.

About 3 times in the last decade have we needed to manually run an update mid-week to address high-risk remote exploits ASAP.  A home user, behind a typical router, with no inbound ports open, wouldn't have been harmed by those exploits.   Generally, waiting until the weekend is fine and prevents getting very early, flawed, patches. Some firmware patches the last few years have been less than great.

Plus, our systems are stable all work-week, so only weekend workers notice any patch problems and IT can correct them before Monday morning when systems need to be stable again.

Most enterprises only patch monthly or quarterly unless there is a very specific, known, exploit being used.  They've known that new is the enemy of stability.  I believe it.

But only you can decide how quickly patches need to be installed for your systems, based on the criticality of each system.

As for the smart stuff, the tool needs 2 steps.
a) run the test
b) ask for the report

If the test was run, you just need to ask for the report.

---

### Post by sniper8752 on 2020-03-07
> **sniper8752 said:**
> Also, tried to do the long test, and just get this:
```
sudo smartctl -t long /dev/nvme0smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-88-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


NVMe device successfully opened


Use 'smartctl -a' (or '-x') to print SMART (and more) information



```
Would you have any ideas on this?

---

### Post by TheFu on 2020-03-07
> **sniper8752 said:**
> Would you have any ideas on this?

Only this:
> Use 'smartctl -a' (or '-x') to print SMART (and more) information

---

