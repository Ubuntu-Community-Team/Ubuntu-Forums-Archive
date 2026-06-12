---
title: "Please help; system keeps locking up."
date: 2009-05-10
forum: General Help
---

### Post by njd4k on 2009-05-10
Please, if you have any ideas at all, or just want to offer moral support, I'd really appreciate it. My installation is getting more and more unstable, and the last few attempts to get help on these forums have gone unanswered.

My system has been crashing. A lot. And I don't know why.

At first I thought it was because my Intel wireless card was incompatible with the new network I've been on the last couple days; but the fix recommended in the Ubuntu documentation didn't seem to work. (As posted here [http://ubuntuforums.org/showthread.php?t=1153018](http://ubuntuforums.org/showthread.php?t=1153018)) So I've been working with wireless networking disabled. For a while that seemed to work, but now it's crashing even with that turned off.

Now looking at my system logs again, I found another message which is consistently entered in syslog right before the system locks up:

```
May 10 16:35:43 nic-laptop ntpdate[6016]: adjust time server 91.189.94.4 offset 0.184165 sec
```

Does this mean anything? I haven't been able to find anything by searching for crashes related to this message.

I haven't been able to find anything on the internet to explain what's wrong. I really, REALLY dont' want to have to wipe my hard drive and reconfigure everything. Please. Please. Help.  :(

---

### Post by spiderbatdad on 2009-05-10
try this command in terminal
```
dmesg > ~/Desktop/dmesg.txt
``` Then paste the file here:
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)
After pasting, copy a link to your paste into next post.

---

### Post by kay-man on 2009-05-10
Unfortunately I can't help you with why your system is crashing, but I think you can safely rule out the message you posted. This is your ntp deamon adjusting the time from an internet time server. As far as I know it's harmless but if you want to be sure you can disable it, obviously.

Other things you might want to look into:
1. Do a memory test
2. Do you have enough free space on your hard drives?
3. Are your drives allright? If they're SMART-enabled you can use smartmontools to get a lot of onfo
4. Disable as many services as you can to see if that helps. Maybe you can narrow the problem down.
5. Post your complete most recent log file after a crash. Maybe someone will spot something
6. This is a long shot but I've heard stories where this actually made a difference. Open the case, clean the inside (always a good idea) and check your cards, or maybe pull them out and stick them back in, and make sure everything connects well

Ah, and don't give up just yet! :-)

---

### Post by renkinjutsu on 2009-05-10
if your system's locking up, it's a good idea to also do a fsck
to do that, type in a virtual terminal
```
sudo init 1
```
drop to root shell and umount your drives/partitions
do a fsck

fsck:
fsck -t *filesystem* -pf /dev/*device*
-t filesystem
-p fix problems without asking
-n make no changes to filesystem
-f force check even when filesystem is marked clean
-y assume yes to all

---

### Post by njd4k on 2009-05-10
Thank you all for responding. I've been using Ubuntu long enough to feel like I know what I'm doing -- until something goes wrong. I still have a Mac OS 9 sense of how to fix things. (Step 1: fiddle with control panel. Step 2: reinstall everything, again.) I feel better just having somebody give me some things to try.


@spiderbatdad: Here is the output from dmesg:

[http://paste.ubuntu.com/169191/](http://paste.ubuntu.com/169191/)

@paulklos: 
1. I tried a memtest yesterday and got a clean bill of health.
2. I have 12 GB available, about 20% of the capacity of the hard drive.
3. The SMART test of my hard drive came back as "passed." (Thanks for telling me about this, though -- I already lost one hard drive on this laptop back when it was a windows machine, thankfully still under warranty.)
4. Yeah. That's what I've been trying to do. :(
5. This is what the debug log says in the moments before the last crash. 

```

May 10 16:34:49 nic-laptop kernel: [   18.365910] ieee80211_crypt: registered algorithm 'TKIP'
May 10 16:34:49 nic-laptop kernel: [   18.666344] HDA Intel 0000:00:1b.0: setting latency timer to 64
May 10 16:35:13 nic-laptop kernel: [   47.972131] eth1: no IPv6 routers present
May 10 16:35:13 nic-laptop kernel: [   48.036074] eth0: no IPv6 routers present
May 10 16:35:34 nic-laptop kernel: [   69.012199] CPU0 attaching NULL sched-domain.
May 10 16:35:34 nic-laptop kernel: [   69.012215] CPU1 attaching NULL sched-domain.
May 10 16:35:34 nic-laptop kernel: [   69.016213] CPU0 attaching sched-domain:
May 10 16:35:34 nic-laptop kernel: [   69.016222]  domain 0: span 0-1 level MC
May 10 16:35:34 nic-laptop kernel: [   69.016227]   groups: 0 1
May 10 16:35:34 nic-laptop kernel: [   69.016238] CPU1 attaching sched-domain:
May 10 16:35:34 nic-laptop kernel: [   69.016242]  domain 0: span 0-1 level MC
May 10 16:35:34 nic-laptop kernel: [   69.016249]   groups: 1 0
May 10 16:35:42 nic-laptop NetworkManager: <debug> [1241987742.516210] periodic_update(): Roamed from BSSID 00:11:21:A9:8E:01 (WSU Wireless) to 00:11:5C:4D:E8:E1 (WSU Wireless) 

```

Are there other logs I should post besides debug?

One thing I noticed is that when I wake up my laptop from suspend mode, the little Dell wifi light turn on, even though in the GUI Network Manager wireless is still disabled; I can make the light go off by re-enabling WiFi and then disabling it again. I wonder whether this is some cousin of the Intel wifi bug, after all? But then I wonder why having an up-to-date kernel and drivers didn't fix it. Still, the Network Manager looks involved.

6. I did change the battery recently. I'm not sure how accessible the rest is -- It's a cheap Dell and it's not easy to tell the intentional openings from the lousy plastic joints sometimes...

@renkinjutsu: I've tried the sudo init 1 command twice now; both times instead of going to a shell the computer seems to start shutting down, but the meter under the ubuntu logo never quite gets there and I have to hard restart. I'm going to burn a new live CD so I can unmount the hard drive and do fsck from there. I'm not sure why I don't get a root shell when I use your command.

Thank you all very much for your help.

---

### Post by spiderbatdad on 2009-05-11
Do you experience the same problems when booting cleanly? There are numerous issues with dells discussed regarding resume from suspend.
[http://ubuntuforums.org/archive/index.php/t-391766.html](http://ubuntuforums.org/archive/index.php/t-391766.html) You should be able to find many more. While you may be able to solve the suspend issue, it is possible some boot option to do with acpi suport will help as well. For now, I would recommend not suspending.

---

### Post by njd4k on 2009-05-11
There are numerous issues with this Dell, period -- I'm sticking with Ubuntu largely because as many problems as I'm having, Windows was worse, and I don't think it was primarily Redmond's fault. The 1505 is just a lemon of a laptop. At least with Ubuntu the peripherals work and the hard drive doesn't fail within months. It's a shame Dell is the biggest manufacturer of machines with Ubuntu already installed, because I'd like to support that when I buy my next computer, but I don't think I'd buy another one of their products, ever. My girlfriend had been a Dell customer for years, but after she saw what happened with this machine she replaced her last Dell with her first Mac.

I had suspend and hibernate issues with 8.04 but it seemed to be okay under 8.10. But maybe not. I'll avoid suspending for a few days to see if the crashes don't happen (with and without wireless activated).

---

### Post by njd4k on 2009-05-11
By the way, did these forums get rid of the "thanks" button? I want to click on it! There needs to be some way to give positive reinforcement to community supporters.

---

### Post by njd4k on 2009-05-12
```
May 11 20:44:23 nic-laptop kernel: [   62.088919] CPU0 attaching NULL sched-domain.
May 11 20:44:23 nic-laptop kernel: [   62.088929] CPU1 attaching NULL sched-domain.
May 11 20:44:23 nic-laptop kernel: [   62.089010] CPU0 attaching sched-domain:
May 11 20:44:23 nic-laptop kernel: [   62.089014]  domain 0: span 0-1 level MC
May 11 20:44:23 nic-laptop kernel: [   62.089017]   groups: 0 1
May 11 20:44:23 nic-laptop kernel: [   62.089023]   domain 1: span 0-1 level CPU
May 11 20:44:23 nic-laptop kernel: [   62.089026]    groups: 0-1
May 11 20:44:23 nic-laptop kernel: [   62.089032] CPU1 attaching sched-domain:
May 11 20:44:23 nic-laptop kernel: [   62.089034]  domain 0: span 0-1 level MC
May 11 20:44:23 nic-laptop kernel: [   62.089039]   groups: 1 0
May 11 20:44:23 nic-laptop kernel: [   62.089043]   domain 1: span 0-1 level CPU
May 11 20:44:23 nic-laptop kernel: [   62.089047]    groups: 0-1
May 11 20:45:49 nic-laptop kernel: [  148.924050] eth1: no IPv6 routers present
May 11 21:22:42 nic-laptop kernel: [ 2361.272086] eth1: no IPv6 routers present
May 11 21:22:43 nic-laptop NetworkManager: <debug> [1242091363.691701] periodic_update(): Roamed from BSSID 00:11:5C:4D:E4:91 (WSU Wireless) to 00:11:21:A9:8E:01 (WSU Wireless) 
May 11 21:30:08 nic-laptop NetworkManager: <debug> [1242091808.578409] periodic_update(): Roamed from BSSID 00:11:5C:4D:E4:91 (WSU Wireless) to 00:11:21:A9:8E:01 (WSU Wireless) 
```

I think it is the wireless driver. I don't know why the fix in the Ubuntu documentation isn't working. I'm going to play with the settings.

---

### Post by njd4k on 2009-05-13
I finally realized I can reinstall the open-source B43 driver. I originally upgraded to Intrepid to install the closed-source driver when B43 couldn't use my shared network; now I have to use B43 to not crash my computer on the current one.

I guess I'll just have to switch drivers every time I move... anyway, marking this as read. (And swearing to find an open wifi card somehow on the next laptop). Thanks again.

Edit: apparently the "solved" feature is gone with the thanks button. Why take away these tools?

---

