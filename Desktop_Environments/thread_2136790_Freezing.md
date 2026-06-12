---
title: "Freezing"
date: 2013-04-18
forum: Desktop Environments
---

### Post by Int3rSys on 2013-04-18
Hello guys,
I'm having an issue for the last couple of days. My computer freezes randomly and the only thing I can do while it freezes is to move the mouse courser (the courser moves with a great delay and I can't do nothing with it), so each time I have to restart the computer.

Can somebody help me please ? 

Thank you !

---

### Post by matt_symes on 2013-04-18
Hi

Take a look in the log files. Look at 

```
/var/log/syslog
```

and 

```
/var/log/dmesg
```

That may provide some clues as to what is happening.

Open a terminal and keep an instance of htop running. Look for any runaway processes. Do the same with iotop.


Kind regards

---

### Post by Int3rSys on 2013-04-18
Thanks for the quick response. It seems that the logs (syslog) are not saved, It shows the logs from the last time I have logged in. How can I change it ?

---

### Post by matt_symes on 2013-04-18
Hi

> **Int3rSys said:**
> Thanks for the quick response. It seems that the logs (syslog) are not saved, It shows the logs from the last time I have logged in. How can I change it ?

That's odd as they are saved on a default Ubuntu installation. 

Did you do anything to the logs ? It may be they are not being saved because of the freezing.

If so that will make it harder to track down. Please double check the log files are there or not.

Can you post the output of

```
ls -l var/log
```

and 

```
date
```

Kind regards

---

### Post by Int3rSys on 2013-04-19
for the /var/logs:

```

-rw-r--r-- 1 root              root   15674 Apr 18 22:13 alternatives.log
-rw-r--r-- 1 root              root   23093 Mar 30 13:00 alternatives.log.1
-rw-r--r-- 1 root              root    6350 Feb 28 22:08 alternatives.log.2.gz
-rw-r----- 1 root              adm        0 Apr 18 16:46 apport.log
-rw-r----- 1 root              adm      897 Apr 18 16:26 apport.log.1
-rw-r----- 1 root              adm      446 Apr 16 00:10 apport.log.2.gz
-rw-r----- 1 root              adm      288 Apr 14 21:44 apport.log.3.gz
-rw-r----- 1 root              adm      260 Apr 14 21:24 apport.log.4.gz
-rw-r----- 1 root              adm      220 Apr 12 12:47 apport.log.5.gz
-rw-r----- 1 root              adm      274 Apr 11 21:07 apport.log.6.gz
-rw-r----- 1 root              adm      261 Mar 28 17:19 apport.log.7.gz
drwxr-xr-x 2 root              root    4096 Apr  1 08:04 apt
-rw-r----- 1 syslog            adm    59268 Apr 19 08:48 auth.log
-rw-r----- 1 syslog            adm    32694 Apr 14 21:23 auth.log.1
-rw-r----- 1 syslog            adm     4073 Apr 11 19:38 auth.log.2.gz
-rw-r----- 1 syslog            adm     5516 Mar 31 07:30 auth.log.3.gz
-rw-r----- 1 syslog            adm     1656 Mar 27 14:17 auth.log.4.gz
-rw-r----- 1 root              adm       31 Oct 17  2012 boot
-rw-r--r-- 1 root              root    3035 Apr 18 22:35 boot.log
-rw-r--r-- 1 root              root   49450 Oct 17  2012 bootstrap.log
-rw-rw---- 1 root              utmp       0 Apr  1 08:05 btmp
-rw-rw---- 1 root              utmp       0 Mar  1 07:41 btmp.1
drwxr-xr-x 2 root              root    4096 Apr  1 08:05 ConsoleKit
drwxr-xr-x 2 root              root    4096 Apr 19 07:56 cups
drwxr-xr-x 2 root              root    4096 Feb 28 23:21 dist-upgrade
-rw-r----- 1 root              adm    65272 Apr 18 22:35 dmesg
-rw-r----- 1 root              adm    66203 Apr 18 22:08 dmesg.0
-rw-r----- 1 root              adm    15755 Apr 18 16:24 dmesg.1.gz
-rw-r----- 1 root              adm    16240 Apr 16 18:45 dmesg.2.gz
-rw-r----- 1 root              adm    15835 Apr 16 16:19 dmesg.3.gz
-rw-r----- 1 root              adm    16263 Apr 16 00:39 dmesg.4.gz
-rw-r--r-- 1 root              root  188493 Apr 18 22:13 dpkg.log
-rw-r--r-- 1 root              root  461208 Mar 30 13:02 dpkg.log.1
-rw-r--r-- 1 root              root  118775 Feb 28 23:21 dpkg.log.2.gz
-rw-r--r-- 1 root              root   32032 Mar 29 22:54 faillog
-rw-r--r-- 1 root              root    3747 Feb 28 23:21 fontconfig.log
drwxr-xr-x 2 root              root    4096 Oct 17  2012 fsck
drwxr-xr-x 2 root              root    4096 Oct 12  2012 hp
drwxr-xr-x 2 root              root    4096 Feb 23 10:45 installer
-rw-r----- 1 syslog            adm  1195332 Apr 18 22:35 kern.log
-rw-r----- 1 syslog            adm   344531 Apr 14 21:24 kern.log.1
-rw-r----- 1 syslog            adm   144373 Apr 11 19:38 kern.log.2.gz
-rw-r----- 1 syslog            adm    43838 Mar 31 00:00 kern.log.3.gz
-rw-r----- 1 syslog            adm    38336 Mar 27 13:56 kern.log.4.gz
-rw-rw-r-- 1 root              utmp  292292 Mar 29 22:54 lastlog
drwxr-xr-x 2 root              root    4096 Apr 18 22:35 lightdm
-rw-r----- 1 syslog            adm        0 Feb 23 10:49 mail.err
-rw-r----- 1 syslog            adm        0 Feb 23 10:49 mail.log
drwxr-xr-x 2 root              root    4096 Feb 23 10:49 news
-rw-r--r-- 1 root              root     861 Feb 23 11:44 nvidia-installer.log
-rw-r--r-- 1 root              root   85602 Apr 18 22:35 pm-powersave.log
-rw-r--r-- 1 root              root   87649 Mar 31 23:51 pm-powersave.log.1
-rw-r--r-- 1 root              root     904 Feb 28 23:38 pm-powersave.log.2.gz
-rw-r--r-- 1 root              root       0 Mar 29 23:48 pycentral.log
drwxr-x--- 3 root              adm     4096 Apr 14 21:26 samba
drwx------ 2 speech-dispatcher root    4096 Aug 21  2012 speech-dispatcher
-rw-r----- 1 syslog            adm     2340 Apr 19 08:33 syslog
-rw-r----- 1 syslog            adm   298315 Apr 19 07:55 syslog.1
-rw-r----- 1 syslog            adm    78433 Apr 18 16:46 syslog.2.gz
-rw-r----- 1 syslog            adm   111196 Apr 16 00:53 syslog.3.gz
-rw-r----- 1 syslog            adm     3463 Apr 15 07:43 syslog.4.gz
-rw-r----- 1 syslog            adm    27896 Apr 14 21:26 syslog.5.gz
-rw-r----- 1 syslog            adm    40950 Apr 13 07:41 syslog.6.gz
-rw-r----- 1 syslog            adm    25508 Apr 12 07:38 syslog.7.gz
-rw-r--r-- 1 root              root  344799 Apr 18 22:35 udev
-rw-r----- 1 syslog            adm        0 Feb 23 10:49 ufw.log
drwxr-xr-x 2 root              root    4096 Feb 23 11:12 unattended-upgrades
drwxr-xr-x 2 root              root   12288 Apr 19 07:56 upstart
-rw-r--r-- 1 root              root    1293 Mar  1 12:19 vbox-install.log
drwxr-xr-x 2 root              root    4096 Apr 18 22:35 vmware
-rw-r--r-- 1 root              root   74406 Apr 15 13:19 vmware-installer
-rw-r--r-- 1 root              root  227428 Apr 18 22:35 vnetlib
-rw-rw-r-- 1 root              utmp   89856 Apr 18 23:58 wtmp
-rw-rw-r-- 1 root              utmp  100224 Mar 31 23:51 wtmp.1
-rw-r--r-- 1 root              root   26913 Apr 19 00:27 Xorg.0.log
-rw-r--r-- 1 root              root   26079 Apr 18 22:09 Xorg.0.log.old
-rw-r--r-- 1 root              root   41637 Feb 23 11:42 Xorg.1.log
```

date:
```

Fri Apr 19 08:50:16 IDT 2013
```

---

### Post by matt_symes on 2013-04-19
Hi

Open a terminal and type

```
sudo apt-get install pastebinit
```

```
cat /var/log/syslog | pastebinit
```

Post the link generated and someone will take a look at the log file for you.

Kind regards

---

### Post by Int3rSys on 2013-04-19
[http://paste.ubuntu.com/5720780/](http://paste.ubuntu.com/5720780/)

Thank you very much, greatly appreciated.

---

### Post by rrich1974 on 2013-04-19
i have had freezing issue and i added "pci=nomsi" in grub.conf 
since that moment (january 2013) the system works perfect! 
(ubuntu 12.04)

---

### Post by matt_symes on 2013-04-19
Hi

Nothing really in the logs.

This a virtual machine or running on bare metal ?

Kind regards

---

### Post by Int3rSys on 2013-04-19
Bare metal. I also have an issue with updates, that I think maybe has to do with the freezing. Sometimes a red triangle exclamation mark pop's up saying the the machine is not updated but it is. Maybe that is what causing the freezing ?

---

### Post by rrich1974 on 2013-04-19
have you tried what i told you?

---

### Post by Int3rSys on 2013-04-19
Sorry mate, didn't see your reply. The grub.cfg is located in /boot/grub ? if so, it doesn't matter where I add it ?

Thanks alot !

---

### Post by rrich1974 on 2013-04-19
right now, i am on a windows machine...
take this:
[https://answers.launchpad.net/ubuntu/+question/108519](https://answers.launchpad.net/ubuntu/+question/108519)
dont forget to run 
> sudo update-grub2

that thing have worked for my machine, i dont know about yours.

---

### Post by Int3rSys on 2013-04-20
It seems that it stopped for a while, I hope it will continue this way.
Thanks guys, you are awesome !

---

### Post by matt_symes on 2013-04-20
Hi

Well if it was message signalled interrupts causing the problem then nomsi was a great shout.

If it does return then post back but, hopefully, that fixed it.

There are many, many things that can cause random freezes.

Kind regards

---

### Post by plbuster on 2013-04-21
> I tried the following without going into Terminal and it seems to work so far..
I'm running Ubuntu 12.10 onan ASUS model K35E (if you want to know more, just let me know...)

Go Dash Home and on the search line, type, "xdiagnose"...(if nothing shows up...check with the Ubuntu Software Center...)
if you're not sure if you have xdiagnose...you can go to the Ubuntu Software Center icon on the left hand menu of icons...(the icon that looks like an orange shopping bag..) press the "Installed" label button, then check the Developers Tools menu...you will probably see xdiagnose at the bottom...(there is a picture of a microscope...)
anyhow...I opened xdiagnose and it popped up with a few choices...

at the bottom is a checkbox with the label "Disable PAT Memory"...
with a popup that reads, "This pagetable extension can interfere with the memory management of proprietary drivers under certain situations and cause lagging or failures to allocate video memory, so turning it off can prevent these problems."

I checked the box...and so far, my computer stopped freezing...

Just so's ya know...I'm running an i5-2430m CPU @ 4.40Ghz x 4
but the "About This Computer" (you can find this on Ubuntu 12.10 in the upper right hand corner of the screen...there is a small icon that looks like a gear...)
says "Graphics Unknown"...

My computer is running an "Integrated Intel GMA HD" graphics whatchamacallit...

I was hitting freezes every few minutes while online (and sometimes offline)...and since I disabled the PAT memory...well...so far so good.

Tell me if you think this is a bad thing.  My computer was originally specifically designed for Windows OSs...and I've grown to despise Window's ability to turn a hard drive into a pile of iron oxide....further...the hard drive had a hardware issue and wouldn't boot every time...so I removed the hard drive and use a Seagate 640 GB FreeAgent GoFlex USB drive (not sure what the techies call the thing but it loads and runs Ubuntu just fine...) that I bought at WalMart....(try doing THAT with Windows...)

[COLOR=#000000]Nope...still freezing...
think I'll try some of the suggestions above...(I'm still keeping PAT off until I'm sure...)
So..I tried rrich1974's suggestion to run sudo update-grub2....if I freeze again...well, let's just say that the color I change the text to won't be orange....
[/COLOR]

---

### Post by rrich1974 on 2013-04-21
offtopic
graphics unknown means that you must install "mesa-utils" 
in fact, ubuntu do see your graphic chipset, but it does not tell you!

but read my entire suggestion, add  'pci=nomsi" and then run "sudo update-grub2"

---

### Post by plbuster on 2013-04-21
[COLOR=#a52a2a]*@rrich1974.....its working....  *
[/COLOR]:(

er...well...no it's not...
hmm...


So...I checked the syslog...
and suprise...I found out several error messages that basically said "GPU hung"...

> [COLOR=#ff0000][/COLOR]Apr 15 13:04:48 patrick-K53E kernel: [ 2108.190101] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung

Apr 15 13:05:06 patrick-K53E kernel: [ 2126.918180] atl1c 0000:03:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.[COLOR=#ff0000]
[/COLOR]
and then went to another thread called, "internal error, GPU hung"...and I'm not the only one...something to do with an update we uploaded at one time or another
so...

---

### Post by matt_symes on 2013-04-21
Hi

> **plbuster said:**
> 
Apr 15 13:04:48 patrick-K53E kernel: [ 2108.190101] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung

Apr 15 13:05:06 patrick-K53E kernel: [ 2126.918180] atl1c 0000:03:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.[COLOR=#ff0000]
[/COLOR]

You have an intel graphics card and the sandybridge arch  ?

This is a known issue. 

It can be fixed by updating your kernel to one of the 3.8.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

There may be other fixes out there by now but updating the kernel is a known fix.

It is unlikely that you PC is old enough or uncommon enough to be affected by msi. random suggestions rarely help and it is much better to actually try and diagnose the issue.

If you need instruction on how to install a new kernel then post back.

Kind regards

---

### Post by rrich1974 on 2013-04-21
@matt symes
i think you are right, i have applied "pci=nomsi" on my laptop that is pretty old (2008), but it is worth to try! you never know....

---

