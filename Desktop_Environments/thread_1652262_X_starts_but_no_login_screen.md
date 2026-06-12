---
title: "X starts but no login screen"
date: 2010-12-24
forum: Desktop Environments
---

### Post by sid.mallya on 2010-12-24
Check the next post. It is the actual problem which I figured out after tinkering around a LOT !

> Hey I updated the Linux kernel yesterday. For some reason, today the GUI was lagging a bit so I decided to restart the computer (it worked in the past). It kinda got stuck at one point of time, so I did a cold (hard?) reboot - by pressing the restart button (hardware) .. 

The computer restarted, Ubuntu 10.04 booted up properly, went to GUI but no login screen. It even gave me the welcome audio.

I am able to log into tty terminals. I tried using "startx" but it gives the "X server is already running at 0, fatal error" message (obviously) .. I tried 

```
rm -rf /tmp/.X0-lock

sudo dpkg-reconfigure xserver-xorg
```

codes but it doesn't help. What should I do ? I am using a liveCD to use the internet right now .. Quick help will be much appreciated.

Update: I have temporarily managed to solve the problem. I realised that "gdm" was not working. So I made kdm as the default desktop manager and I am currently using KDE.

Gnome is still not functioning properly with panels applets not loading, compiz not working correctly and obviously GDM still not recognising users.

There are the two errors it gave me -->

```
gdm-binary[2287]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
gdm-binary[2287]: WARNING: Unable to find users: no seat-id found
gdm-binary[2287]: WARNING: GdmDisplay: display lasted 0.052473 seconds
```

and 

```
** (gdm-binary:2536): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.58" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:2536): WARNING **: Could not acquire name; bailing out
```

---

### Post by sid.mallya on 2010-12-24
Hey .. I run a Ubuntu 10.04 distro on my desktop computer. I updated my linux kernel from "2.6.32-21-generic" to "2.6.32-27-generic" yesterday along with some other updates which GNOME suggested me to do. 

I then went on to restart the computer, which for some reason took a LOT of time so I just restarted it using the hardware restart button. (Mostly probably mistake #1)

Anywho, this is when the trouble began. The Gdm fails to starts but X server does start up properly. All I get is a purple screen with the cursor but no login screen. I am able to log into tty though.

Here, I ran the "service gdm stop" command and then "startx" and got logged into Gnome right away. Now, Gnome does work but the panel applets crash, compiz got disabled on its own and most system programs like "Synaptic package manager", "System monitor" etc. do not open, or if they do, not for more than a few seconds.

For now, I have made kdm (I have KDE too) as the default desktop manager and am using KDE to access the GUI. Everything is working fine in KDE but still system programs like the ones I mentioned before are not working .. 

What should I do ?

---

### Post by sid.mallya on 2010-12-24
My kernel version is 2.6.32-21-generic and after update it is '2.6.32-27-generic'

And my video card is "00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)"

---

### Post by sid.mallya on 2010-12-24
> **sid.mallya said:**
> And my video card is "00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)"

I think the kernel version is x.27 not x.21 but uname -r gave me x.21 .. so go figure. :s

---

### Post by sid.mallya on 2010-12-25
Bump .. Oh c'mon .. Show me some love too  .. :( .. I have an exam on Monday and I need to work with the software installed on the OS .. the liveCD can only do so much ..

---

### Post by sid.mallya on 2010-12-25
Okay .. I reinstalled the gnome-session and did some updates again from the recovery mode and was able to log into the computer .. Lets see what happens when I restart the computer again .. 

Fingers crossed.

Update: Nope .. Still no login screen. It gets stuck at the pinkish screen with just the mouse cursor. I have log into tty terminal, stop the gdm service and startx .. If I stop gdm and again start it, it sends me back to the pink screen with no login.

Wtf do I do ?

---

### Post by WthIteh on 2010-12-25
You could try (re)moving xorg conf and let do the default actions (by vesa) by
```

cd /etc/X11/
sudo mv xorg.conf xorg.conf.old

```Do it from a tty login and then startx.
If not work, from a tty login go to
```

sudo aptitude

```and try to find any graphic card driver and remove them. Extra non-related drivers could cause problems.

Also let us see result of
```

dmesg

```after a failed startx if above solutions do not work.

---

### Post by sid.mallya on 2010-12-25
Finally ! Thanks for the reply. Okay .. So here's the thing, after tinkering around a LOT .. I finally figured out the exact problem .. So here it is -->

1. My gdm is failing to start for reasons unknown .. So if I go to tty and stop the service (gdm) then "startx" .. I get logged into Gnome directly. BUT, there are significant issues with Gnome. Compiz fails to start correctly, applets of the panel crash and system programs like package manager, system monitor etc. do no open, or if they do, not for more than a few seconds.

2. For now, I have made KDM my default desktop manager and am able to log into KDE .. KDE is working fine, altho the system programs are still not working here.

Do I need to do the same things for my problem, still ? Also, i do not have a xorg.conf file in /etc/X11 .. From my understanding Ubuntu no longer requires it. I do have the xorg.conf.failsafe file.

---

### Post by rivera151 on 2010-12-25
I'm having the same problem, except that I have kde installed and now I can't log in. I haven't tried installing gnome to check, but so far I'm having the same exact problem you are. 

[EDIT]
I ran the LiveCD installer without formatting the partitions (I have a / and a /home partition) and It was fixed quite fast. Of course, make sure you use your same user name. Good luck!

---

### Post by sid.mallya on 2010-12-26
I have only one partition for the Linux OS .. Tell me, wouldn't reinstalling the OS cause me to lose my data ?

---

### Post by WthIteh on 2010-12-26
> **sid.mallya said:**
> I have only one partition for the Linux OS .. Tell me, wouldn't reinstalling the OS cause me to lose my data ?
If you have just **one** partition, reinstalling **will remove** all of your data in that partition.
Also reinstalling is rarely the correct solution in Linux world. You should fix what was changed. In config files, etc.

Did you check result of
```
dmesg
```Any clue?

Also you may try Ctrl+Alt+T when you login in gnome (without any panel, etc.) to open a terminal. If it works, you could run any program from terminal instead of applets (for saving time) like entering
```
firefox
```there for running firefox, etc.

You could also try Alt+F2 for running programs if the above one does not work.

> Do I need to do the same things for my problem, still ? Also, i do not  have a xorg.conf file in /etc/X11 .. From my understanding Ubuntu no  longer requires it. I do have the xorg.conf.failsafe file.Gnome never required xorg.conf but you could use it for reseting to vesa mode.
You may try
```

cd /etc/X11
sudo mv xorg.conf.failsafe xorg.conf

```for reseting to vesa too.

Another solution is to remove **.gnome2** folder from you home directory to reset gnome configuration. If it works you need to add applets to your panel again.

---

### Post by sid.mallya on 2010-12-26
Firefox and other such programs are running .. Cause they are not dependent on Ubuntu-gnome .. System Monitor, Synaptic Package Manager, etc. aren't working.

Terminal is working though .. I tried reinstalling ubuntu-desktop but it didn't help .. I also did what you asked me to do, also didn't help.

The dmesg output is this -->

```
[   44.455714] ISO 9660 Extensions: RRIP_1991A
[   51.743886] lo: Disabled Privacy Extensions
[ 1063.625848] lo: Disabled Privacy Extensions
[ 5692.087272] lo: Disabled Privacy Extensions
[ 6281.648313] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[ 6281.648317] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 6281.772506] atkbd.c: Unknown key released (translated set 2, code 0x88 on isa0060/serio0).
[ 6281.772509] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[ 6359.888670] EXT4-fs (sda3): mounted filesystem with ordered data mode
[ 6379.473467] __ratelimit: 18 callbacks suppressed
[ 6379.473472] gedit[2673]: segfault at 1c4f ip 00dd1fc4 sp bfdca578 error 4 in libc-2.11.1.so[cb7000+153000]
[ 6498.953092] kwrited[1529]: segfault at c9a3456d ip 00fd28bb sp bfb8532c error 5 in libc-2.11.1.so[f67000+153000]
[ 6513.245335] nm-applet[2909]: segfault at 1c4f ip 04851fc4 sp bffd6878 error 4 in libc-2.11.1.so[4737000+153000]
[ 6515.081858] bonobo-activati[2960]: segfault at 1c4f ip 0041efc4 sp bfd9a4c8 error 4 in libc-2.11.1.so[304000+153000]
[ 6515.204369] bonobo-activati[2966]: segfault at 1c4f ip 0064afc4 sp bff576f8 error 4 in libc-2.11.1.so[530000+153000]
[ 6515.229193] bonobo-activati[2969]: segfault at 1c4f ip 00b5bfc4 sp bfa62888 error 4 in libc-2.11.1.so[a41000+153000]
[ 6515.251438] bonobo-activati[2972]: segfault at 1c4f ip 00b0afc4 sp bff01828 error 4 in libc-2.11.1.so[9f0000+153000]
[ 6515.433520] CPU0 attaching NULL sched-domain.
[ 6515.433526] CPU1 attaching NULL sched-domain.
[ 6515.456055] CPU0 attaching sched-domain:
[ 6515.456058]  domain 0: span 0-1 level MC
[ 6515.456061]   groups: 0 1
[ 6515.456066] CPU1 attaching sched-domain:
[ 6515.456068]  domain 0: span 0-1 level MC
[ 6515.456071]   groups: 1 0
[ 6519.309824] bonobo-activati[2991]: segfault at 1c4f ip 008a6fc4 sp bf91c5a8 error 4 in libc-2.11.1.so[78c000+153000]
[ 6519.355252] bonobo-activati[2994]: segfault at 1c4f ip 004bffc4 sp bf9b7ef8 error 4 in libc-2.11.1.so[3a5000+153000]
[ 6519.403272] bonobo-activati[2997]: segfault at 1c4f ip 00ad5fc4 sp bfb33c08 error 4 in libc-2.11.1.so[9bb000+153000]
[ 6519.448231] bonobo-activati[3000]: segfault at 1c4f ip 004bdfc4 sp bff136c8 error 4 in libc-2.11.1.so[3a3000+153000]
[ 6537.291257] lo: Disabled Privacy Extensions
[ 6537.453944] lo: Disabled Privacy Extensions
[ 6544.318893] bonobo-activati[3106]: segfault at 1c4f ip 00719fc4 sp bfae5d38 error 4 in libc-2.11.1.so[5ff000+153000]
[ 6544.324925] bonobo-activati[3109]: segfault at 1c4f ip 0091ffc4 sp bfd08118 error 4 in libc-2.11.1.so[805000+153000]
[ 6544.331032] bonobo-activati[3112]: segfault at 1c4f ip 0064dfc4 sp bf820c98 error 4 in libc-2.11.1.so[533000+153000]
[ 6544.360150] bonobo-activati[3115]: segfault at 1c4f ip 006a1fc4 sp bfa2f048 error 4 in libc-2.11.1.so[587000+153000]
[ 6544.365852] bonobo-activati[3118]: segfault at 1c4f ip 00819fc4 sp bfc4ac38 error 4 in libc-2.11.1.so[6ff000+153000]
[ 6544.371332] bonobo-activati[3121]: segfault at 1c4f ip 00526fc4 sp bfdff838 error 4 in libc-2.11.1.so[40c000+153000]
[ 6988.217257] bonobo-activati[3605]: segfault at 1c4f ip 0081bfc4 sp bf9e5ae8 error 4 in libc-2.11.1.so[701000+153000]
[ 6988.217618] gnome-panel[2899]: segfault at 4 ip 080ad2f9 sp bfdf4a40 error 4 in gnome-panel[8048000+83000]
[ 6988.488776] bonobo-activati[3609]: segfault at 1c4f ip 0092efc4 sp bf999e68 error 4 in libc-2.11.1.so[814000+153000]
[ 6988.543251] bonobo-activati[3612]: segfault at 1c4f ip 003affc4 sp bff244d8 error 4 in libc-2.11.1.so[295000+153000]
[ 6988.569989] bonobo-activati[3615]: segfault at 1c4f ip 006c2fc4 sp bfcdc0f8 error 4 in libc-2.11.1.so[5a8000+153000]
[ 6988.595340] bonobo-activati[3618]: segfault at 1c4f ip 0078efc4 sp bfd6d6d8 error 4 in libc-2.11.1.so[674000+153000]
[ 6988.687090] bonobo-activati[3621]: segfault at 1c4f ip 009d3fc4 sp bfb34788 error 4 in libc-2.11.1.so[8b9000+153000]
[ 6988.713894] bonobo-activati[3624]: segfault at 1c4f ip 00649fc4 sp bfd0ebf8 error 4 in libc-2.11.1.so[52f000+153000]
[ 6988.740066] bonobo-activati[3627]: segfault at 1c4f ip 0062afc4 sp bfe777a8 error 4 in libc-2.11.1.so[510000+153000]
[ 6988.764698] bonobo-activati[3630]: segfault at 1c4f ip 00f48fc4 sp bfefaf88 error 4 in libc-2.11.1.so[e2e000+153000]
[ 7181.610710] bonobo-activati[3760]: segfault at 1c4f ip 009c9fc4 sp bfa05b38 error 4 in libc-2.11.1.so[8af000+153000]
[ 7181.611079] gnome-panel[3607]: segfault at 4 ip 080ad2f9 sp bfda90f0 error 4 in gnome-panel[8048000+83000]
[ 7181.811595] bonobo-activati[3764]: segfault at 1c4f ip 005ecfc4 sp bfce2d68 error 4 in libc-2.11.1.so[4d2000+153000]
[ 7181.849387] bonobo-activati[3767]: segfault at 1c4f ip 004c2fc4 sp bf924948 error 4 in libc-2.11.1.so[3a8000+153000]
[ 7181.875288] bonobo-activati[3770]: segfault at 1c4f ip 0066bfc4 sp bfa04ed8 error 4 in libc-2.11.1.so[551000+153000]
[ 7181.900460] bonobo-activati[3773]: segfault at 1c4f ip 008cdfc4 sp bfa79bd8 error 4 in libc-2.11.1.so[7b3000+153000]
[ 7181.957632] bonobo-activati[3776]: segfault at 1c4f ip 00951fc4 sp bfeb0be8 error 4 in libc-2.11.1.so[837000+153000]
[ 7181.982831] bonobo-activati[3779]: segfault at 1c4f ip 00524fc4 sp bf8a0798 error 4 in libc-2.11.1.so[40a000+153000]
[ 7182.008858] bonobo-activati[3782]: segfault at 1c4f ip 004c9fc4 sp bfa361e8 error 4 in libc-2.11.1.so[3af000+153000]
[ 7182.034712] bonobo-activati[3785]: segfault at 1c4f ip 0044afc4 sp bffc2da8 error 4 in libc-2.11.1.so[330000+153000]

```

Apparently there are many seg-faults .. I have posted only the last bit of the message ..

---

### Post by WthIteh on 2010-12-26
Two solutions:
1. Do this
```

cd ~
mkdir backup
mv .gconf .gconfd .gnome2 .gnome2_private/ backup

```
and then restart computer.
2. Use "aptitude" (in terminal) instead of "synaptic" and
reinstall "gnome-desktop-environment" package.

---

### Post by sid.mallya on 2010-12-26
I am beginning to think maybe its me who is fcuking this up..

I pressed "g" after selecting gnome in aptitute and it got removed .. !? .. Now, when I press 'g' again to install it .. it gives me this error -->

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages

```

When I try to do this -->

```
siddharth@siddharth-desktop:~$ sudo aptitude reinstall gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
gnome is not currently installed, so it will not be reinstalled.
gnome is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

Update -->

```
siddharth@siddharth-desktop:~$ dpkg -l ubuntu-desktop
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-=======================-==============================================================
ii  ubuntu-desktop          1.197                   The Ubuntu desktop system

```

---

### Post by rivera151 on 2010-12-26
don't delete the partition, and don't format it. you will lose your installed programs, but your settings and data should be alright. you should be back up important stuff just in case, but it shouldn't mess with your documents and settings. at least that's how it worked for me.
Good Luck

---

### Post by WthIteh on 2010-12-26
OK, first run the aptitude in terminal without any argument
```
sudo aptitude
```Then you will see a window in the terminal like synaptic. It will show you **in red** that there is a package dependency problem. First press **u** to update.
Then press **e** to examine the problem. Use **.** and **,** for selecting different solutions. When you found the right solution (installing missed packages) press **!** to select it and two **g** to apply it.
When fixed and red notification removed run
```

sudo aptitude update
sudo aptitude upgrade
sudo aptitude reinstall gnome-desktop-environment

```
I hope it fix it.

---

### Post by sid.mallya on 2010-12-26
```
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found

```

There is some problem here .. =/

Otherwise, it is installing Gnome now .. Ill update this post to let u know what happens .. :)

Thanks for the help ..

---

### Post by sid.mallya on 2010-12-26
Process completed .. But GNOME still has the same problem. Panel applets crash, if I try to "add to panel", the panel crashes, reloads and again crashes all the applets. 

What now ? :(

---

### Post by AbeJarano on 2010-12-26
Thanks, I'm going to try changing my Desktop to KDE for my problem temp fix.

But can you check the log files in /var/log and see if there are any errors in the latest Xorg.?.log, syslog and daemon.log?

---

### Post by rivera151 on 2010-12-26
> **WthIteh said:**
> If you have just **one** partition, reinstalling **will remove** all of your data in that partition.
Also reinstalling is rarely the correct solution in Linux world. You should fix what was changed. In config files, etc.


This is true. However, all the things posted here I had tried (before  going online to get help) with the same results.  But I do agree with you, and I was surprised I had to pull out an installer CD, but the process was rather painless.

I believe the problem was with apt, something got corrupted in it.  And since it was apt that was broken, nothing could update, so nothing could reinstall.  I figured the installer would overwrite the corrupted apt installation, and it did.

I mentioned that I had my / and /home on different partitions, however, I don't think I had to use this scheme, as I didn't have to wipe my / (or /home) partition, and I believe the installer does not delete anything under /home.  However, should this not have worked, I could have wiped my / partition and left my /home without formatting and would have been able to keep my data on a fresh, wiped installation.  Since the OPs data is on the same partition, this option would not be available for the OP.

@sid.mallya
With regards to reinstalling, during the install process the installer looks for directories to which it needs to write, and if they are created (**which they are if you chose not to format the partition in the partitioning section of the installer**), it overwrites the files in those directories.  It doesn't delete other stuff.  I think /usr/bin and /usr/lib and other binary directories are completely wiped and overwritten (gives you the stock packages), but others, like your home directory, it doesn't have a reason to mess with it.  For example, grub found the updated kernel (2.6.35-24) and added it to the grub list, which required me to reboot and choose the installer kernel rather than the latest kernel to finally get the system running and then "sudo aptitude update;  sudo aptitude safe upgrade".  After that, had to reinstall java and adobe, I'm sure there's some other packages I have to reinstall.  But my desktop, files, settings were intact.  It wouldn't hurt to backup important stuff, just in case, but I think you should be able to do this no problem.  If most/all software is from a package manager, you shouldn't have a problem.

Any feedback or corrections welcome, but I do believe that's how it went down. :-k Use instructions at your own judgement and risk, as always.

---

### Post by sid.mallya on 2010-12-27
^ Thanks for the info mate .. Is there anything else I can try ? I wanna keep reinstall as the very last option ..

---

### Post by rivera151 on 2010-12-27
Try:
```

sudo aptitude purge ubuntu-desktop
sudo aptitude autoclean
sudo aptitude clean
sudo aptitude install ubuntu-desktop

```

That will uninstall ubuntu-desktop (should be a gang of packages), including configuration files of all packages, then it will delete old packages, then it will delete all packages in the cache (forcing them to be downloaded in case one of the packages is corrupted), and then redownload and reinstall. If that doesn't fix you up you may need to seek greater guidance to avoid reinstalling.

Good luck!

---

### Post by sid.mallya on 2010-12-27
Thanks bro .. But no it didn't help.

---

### Post by rivera151 on 2010-12-27
I didn't think it would. Well, like I said, you should run the installer, and choose an advanced partitioning scheme option. When you see the partition list, select your partition (do not add/remove partitions) and edit its properties. You want to specify an ext4 (or ext3 if you have an ext3) partition, uncheck the "Format partition" option, and tell it that the mount point is /. Make sure your swap is assigned also if you have a swap partition. That should reinstall the system without messin with your documents. Still, BACK UP IMPORTANT DOCS. Let me know if that works, I dont see why It shouldn't.

---

### Post by rivera151 on 2010-12-29
Can you get on tty1, tty2, etc, like I could?  Do you know how you can backup important docs to a usb from tty*/terminal?

---

