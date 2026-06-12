---
title: "Constant hard drive activity"
date: 2005-06-25
forum: Desktop Environments
---

### Post by steveman on 2005-06-25
Hi,

I've just done a fresh install on my new machine and for some reason I am yet to determine, the system seems to need a very short hard drive access, approx every 3-5 seconds.  This is while there is no activity at all - just logged in under GNOME.

Using a SATA drive partitioned with swap and ext3 filesystem.  The system definitely isn't using any swap space at this time either. There does not seem to be anything getting written to /var/log either.

Have read some notes on this in other threads and have tried:

* Using noatime, nodiratime in /etc/fstab.  This seemed to improve but did not remove the symptoms.
* Stopped dbus-l - no effect.
* Stopping a wide variety of other things - no effect.
* Using laptop-mode.  This seems to almost completely remove the problem.  However, this is a desktop machine and doesn't seem to be what I want to do....

Any ideas?

---

### Post by NotSoSuperUser on 2005-06-25
Could it be because you are using Ext3 and it is journaling your hard drive?

---

### Post by skoal on 2005-06-25
Can you post back (in quotes) what 'ps -ely' shows?

\\//_

---

### Post by steveman on 2005-06-26
[QUOTE=skoal]Can you post back (in quotes) what 'ps -ely' shows?

\\//_

[/QUOTE]

Output shown below - sorry wasn't sure what you meant by in quotes....

Below that is /etc/fstab in case this is of help.

S   UID   PID  PPID  C PRI  NI   RSS    SZ WCHAN  TTY          TIME CMD
S     0     1     0  0  76   0   508   388 -      ?        00:00:00 init
S     0     2     1  0  94  19     0     0 ksofti ?     00:00:00 ksoftirqd/0
S     0     3     1  0  65 -10     0     0 worker ? 00:00:00 events/0
S     0     4     3  0  67 -10     0     0 worker ? 00:00:00 khelper
S     0    22     3  0  75 -10     0     0 worker ? 00:00:00 kacpid
S     0   121     3  0  65 -10     0     0 worker ? 00:00:00 kblockd/0
S     0   159     3  0  80   0     0     0 pdflus ?       00:00:00 pdflush
S     0   160     3  0  75   0     0     0 pdflus ?       00:00:00 pdflush
S     0   162     3  0  74 -10     0     0 worker ? 00:00:00 aio/0
S     0   161     1  0  75   0     0     0 kswapd ?        00:00:00 kswapd0
S     0   749     1  0  75   0     0     0 serio_ ?  00:00:00 kseriod
S     0   894     3  0  65 -10     0     0 worker ? 00:00:00 ata/0
S     0   902     1  0  85   0     0     0 -      ?        00:00:00 scsi_eh_0
S     0   903     1  0  85   0     0     0 -      ?        00:00:00 scsi_eh_1
S     0   943     1  0  75   0     0     0 kjourn ?     00:00:00 kjournald
S     0   970     1  0  74 -10   368   383 -      ?        00:00:00 udevd
S     0  2127     1  0  75   0     0     0 -      ?        00:00:00 khpsbpkt
S     0  3202     1  0  75   0     0     0 kjourn ?     00:00:00 kjournald
S     0  3883     1  0  81   0     0     0 -      ?        00:00:00 shpchpd_event
S     0  4034     1  0  76   0     0     0 -      ?        00:00:00 knodemgrd_0
S     0  4351     1  0  75   0     0     0 hub_th ?    00:00:00 khubd
S     0  5593     1  0  65 -10   976   535 -      ?        00:00:00 dhclient3
S     0  6036     1  0  76   0   380   388 syslog ?        00:00:00 dd
S   106  6038     1  0  76   0  1464   608 pipe_w ?     00:00:00 klogd
S     0  6074     1  0  76   0  2376  2531 -      ?        00:00:00 gdm
S     0  6087  6074  0  76   0  2820  2613 -      ?        00:00:00 gdm
S     0  6122  6087  0  75   0 25064  7562 -      ?        00:00:01 Xorg
S   101  6711     1  0  75   0  1048   530 -      ?        00:00:00 dbus-daemon-1
S   111  6724     1  0  76   0  6244  1922 -      ?        00:00:00 hald
S     0  6737     1  0  80   0   432   386 rt_sig ? 00:00:00 inetd
S     0  6883     1  0  77   0  1144   748 -      ?        00:00:00 master
S   100  6896  6883  0  76   0  1068   750 -      ?        00:00:00 pickup
S   100  6897  6883  0  76   0  1096   758 -      ?        00:00:00 qmgr
S     1  7145     1  0  81   0   608   432 -      ?        00:00:00 atd
S     0  7156     1  0  76   0   816   446 -      ?        00:00:00 cron
S     0  7178     1  0  77   0   472   387 -      tty1     00:00:00 getty
S     0  7179     1  0  77   0   472   387 -      tty2     00:00:00 getty
S     0  7180     1  0  77   0   472   387 -      tty3     00:00:00 getty
S     0  7181     1  0  76   0   472   387 -      tty4     00:00:00 getty
S     0  7182     1  0  76   0   472   387 -      tty5     00:00:00 getty
S     0  7183     1  0  76   0   472   387 -      tty6     00:00:00 getty
S  1000  7380  6087  0  75   0  9196  4393 -      ?        00:00:00 x-session-manag
S  1000  7425  7380  0  76   0   892   748 -      ?        00:00:00 ssh-agent
S  1000  7428     1  0  76   0   720   638 -      ?        00:00:00 dbus-launch
S  1000  7429     1  0  79   0   736   504 -      ?        00:00:00 dbus-daemon-1
S  1000  7431     1  0  76   0  8164  2710 -      ?        00:00:00 gconfd-2
S  1000  7434     1  0  79   0   984   568 -      ?        00:00:00 gnome-keyring-d
S  1000  7436     1  0  76   0  4024  1331 -      ?        00:00:00 esd
S  1000  7438     1  0  76   0  2776  1553 -      ?        00:00:00 bonobo-activati
S  1000  7440     1  0  76   0  8380  4709 -      ?        00:00:00 gnome-settings-
S  1000  7443     1  0  75   0  1192   596 -      ?        00:00:00 gam_server
S  1000  7451     1  0  76   0  2144  1168 -      ?        00:00:00 xscreensaverS  1000  7478     1  0  76   0  2716  1931 -      ?        00:00:00 gnome-smproxy
S  1000  7480     1  0  76   0  6900  3216 -      ?        00:00:00 metacity
S  1000  7488     1  0  75   0 10760  6644 -      ?        00:00:00 gnome-panel
S  1000  7490     1  0  75   0 16852  9057 -      ?        00:00:00 nautilus
S  1000  7492     1  0  75   0  7036  4065 -      ?        00:00:00 gnome-volume-ma
S  1000  7517     1  0  76   0  9316  4357 -      ?        00:00:00 update-notifier
S  1000  7537     1  0  75   0  7632  8405 -      ?        00:00:00 gnome-cups-icon
S  1000  7557     1  0  76   0  9668  4451 -      ?        00:00:00 wnck-applet
S  1000  7559     1  0  75   0  8744  6618 -      ?        00:00:00 trashapplet
S  1000  7563     1  0  76   0  3576  4062 -      ?        00:00:00 gnome-vfs-daemo
S  1000  7573     1  0  76   0   736   554 -      ?        00:00:00 mapping-daemon
S  1000  7580     1  0  75   0  7560  4118 -      ?        00:00:00 notification-ar
S  1000  7582     1  0  76   0  9000  4609 -      ?        00:00:00 clock-appletS     0  7885     1  0  93  10   788   420 -      ?        00:00:00 acpid
S   102  7917     1  0  85  10  2528  1388 -      ?        00:00:00 cupsd
R  1000  7964     1  0  76   0 12952  7662 -      ?        00:00:00 gnome-terminal
S  1000  7965  7964  0  78   0   656   556 -      ?        00:00:00 gnome-pty-helpe
R  1000  7966  7964  0  76   0  1684  1021 -      pts/0    00:00:00 bash
S   105  8040     1  0  86  10   740   435 -      ?        00:00:00 syslogd
R  1000  8062  7966  0  76   0   856   913 -      pts/0    00:00:00 ps

/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    errors=remount-ro,noatime,nodiratime 0      1
/dev/sda3       /home           ext3    noatime,nodiratime        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by skoal on 2005-06-26
Ooops! The operable word there was "quote".  It helps when posting such long configuration settings (like "xorg.conf" or even this), to wrap your response using the "quote" feature vbulletin provides.  No problemo...

As far as your constant IDE access, try shutting down the "dbus-1" init script:

sudo /etc/init.d/dbus-1 stop

That should kill off the "hald" daemon and 1 other, I can't remember.  ** However, when you do this, every time you log back into Gnome, you will get "dbus" or "hal" warnings/errors.  You will more than likely lose some functionality.  I only provide this option to hopefully see if it resolves your concern, as it was for me, and which helped in my case.  It may or may not help in yours.  I use another DE called XFCE so having those "services" running for me is not an issue.

"caveat emptor"...or better yet..."Abusus non tollit usum" - Wrong use does not preclude proper use...

\\//_

---

### Post by virgule on 2005-06-26
Let me join this thread. I have these symptoms too but only when in GNOME or Xfce4. KDE does not.. gkrellm reveal a steady [35...60]kb write every 5 seconds. Also, in /var/log/messages -- MARK -- is print every 20 minutes:
```

Jun 26 00:38:07 localhost -- MARK --
Jun 26 00:58:07 localhost -- MARK --
Jun 26 01:18:07 localhost -- MARK --

```

Please, examine this output for me, I found it weird it has that many evolutions, bdus-deamons, pgp-agents and xmms. The later being not even loaded. 

```

# ps -ely
S   UID   PID  PPID  C PRI  NI   RSS    SZ WCHAN  TTY          TIME CMD
S     0     1     0  0  76   0   564   423 select ?        00:00:01 init
S     0     2     1  0  94  19     0     0 ksofti ?     00:00:00 ksoftirqd/0
S     0     3     1  0  65 -10     0     0 worker ? 00:00:03 events/0
S     0     4     3  0  66 -10     0     0 worker ? 00:00:00 khelper
S     0    33     3  0  65 -10     0     0 worker ? 00:00:00 kblockd/0
S     0    69     3  0  75   0     0     0 pdflus ?       00:00:00 pdflush
S     0    70     3  0  75   0     0     0 pdflus ?       00:00:00 pdflush
S     0    72     3  0  75 -10     0     0 worker ? 00:00:00 aio/0
S     0    71     1  0  75   0     0     0 kswapd ?        00:00:00 kswapd0
S     0   360     1  0  75   0     0     0 kjourn ?     00:00:00 kjournald
S     0   392     1  0  65 -10   392   417 select ?        00:00:00 udevd
S     0  1427     1  0  75   0     0     0 scsi_e ? 00:00:03 scsi_eh_0
S     0  1539     1  0  75   0     0     0 hpsbpk ? 00:00:00 khpsbpkt
S     0  2411     1  0  75   0     0     0 kjourn ?     00:00:00 kjournald
S     0  2916     1  0  81   0     0     0 scsi_e ? 00:00:00 scsi_eh_1
S     0  2965     1  0  66 -10  1076   612 select ?        00:00:00 dhclient3
S     0  3259     1  0  75   0     0     0 nodemg ? 00:00:00 knodemgrd_0
S     0  3359     1  0  75   0     0     0 hub_th ?    00:00:00 khubd
S   105  4270     1  0  76   0   804   538 select ?        00:00:00 syslogd
S     0  4285     1  0  76   0   424   423 syslog ?        00:00:00 dd
S   106  4287     1  0  76   0  1600   657 pipe_w ?     00:00:00 klogd
S     0  4323     1  0  76   0  3128  3485 poll   ?        00:00:00 gdm
S     0  4325  4323  0  76   0  3868  3719 select ?        00:00:00 gdm
S     0  4510  4325  7  76   0 20828  5754 select ?        00:16:46 Xorg
S   101  4553     1  0  75   0  1148   662 poll   ?        00:00:00 dbus-daemon-1
S   111  4565     1  0  76   0  6868  2352 poll   ?        00:00:22 hald
S     0  4597     1  0  78   0   484   420 rt_sig ? 00:00:00 inetd
S     1  4654     1  0  76   0   712   535 nanosl ?     00:00:00 atd
S     0  4671     1  0  76   0   916   585 nanosl ?     00:00:00 cron
S     0  4688     1  0  77   0   540   422 read_c tty1  00:00:00 getty
S     0  4689     1  0  76   0   540   422 read_c tty2  00:00:00 getty
S  1000  4815     1  0  79   0   876  1037 select ?        00:00:00 gpg-agent
S  1000  4846     1  0  75   0  1116   662 poll   ?        00:00:00 dbus-daemon-1
S  1000  4865     1  0  76   0  4916  2275 poll   ?        00:00:03 gconfd-2
S  1000  5278     1  0  80   0   876  1037 select ?        00:00:00 gpg-agent
S  1000  5309     1  0  75   0  1116   662 poll   ?        00:00:00 dbus-daemon-1
S  1000  5507     1  0  75   0   876  1037 select ?        00:00:00 gpg-agent
S  1000  5688     1  0  84   0   876  1037 select ?        00:00:00 gpg-agent
S  1000  5719     1  0  75   0  1116   662 poll   ?        00:00:00 dbus-daemon-1
S  1000  5799  4325  0  76   0  1500  1048 wait   ?        00:00:00 startkde
S  1000  5850     1  0  77   0   876  1037 select ?        00:00:00 gpg-agent
S  1000  5853  5799  0  76   0  1028   935 select ?        00:00:00 ssh-agent
S  1000  5856     1  0  76   0  1120   662 poll   ?        00:00:00 dbus-daemon-1
S  1000  5857     1  0  76   0   828   780 select ?        00:00:00 dbus-launch
S  1000  5881     1  0  76   0 11372  7071 select ?        00:00:01 kdeinit
S  1000  5884     1  0  76   0 10080  6834 select ?        00:00:00 dcopserver
S  1000  5886  5881  0  76   0 11268  7310 select ?        00:00:00 klauncher
S  1000  5889     1  0  75   0 16588  8659 select ?        00:00:08 kded
S  1000  5891     1  0  76   0  1908   888 poll   ?        00:00:00 gam_server
S  1000  5899  5881  0  75   0  7160  3893 select ?        00:00:02 artsd
S  1000  5901     1  0  76   0 13628  7478 select ?        00:00:02 kaccess
S  1000  5902  5799  0  76   0   380   417 nanosl ?     00:00:00 kwrapper
S  1000  5904     1  0  76   0 13968  7529 select ?        00:00:02 ksmserver
S  1000  5905  5881  0  75   0 16164  8120 select ?        00:00:15 kwin
S  1000  5907     1  0  75   0 19028  8759 select ?        00:00:20 kdesktop
S  1000  5909     1  1  75   0 22900  9585 select ?        00:00:49 kicker
S  1000  5910  5881  0  76   0 12048  7219 select ?        00:00:00 kio_file
S  1000  5914     1  0  76   0 14872  7839 select ?        00:00:05 klipper
S  1000  5916  5881  5  75   0  9388  5065 poll   ?        00:03:34 gkrellm
S  1000  5920     1  0  75   0 17428  8396 select ?        00:00:06 kmix
S  1000  5922     1  0  76   0 16236  8264 select ?        00:00:03 kio_uiserver
S  1000  5938  5881 16  75   0 33160 11354 select ?        00:10:14 opera
S  1000  5948  5938  0  76   0 33160 11354 poll   ?        00:00:00 opera
S     0  5957     1  0  76   0  2632  1737 poll   ?        00:00:00 gconfd-2
S  1000  5964     1  0  76   0  3268  2159 poll   ?        00:00:00 bonobo-activati
S  1000  5966     1  0  76   0  6888  8308 poll   ?        00:00:00 evolution-data-
S  1000  5967  5966  0  76   0  6888  8308 poll   ?        00:00:00 evolution-data-
S  1000  5968  5967  0  76   0  6888  8308 poll   ?        00:00:00 evolution-data-
S  1000  5977     1  0  76   0 11032  8410 poll   ?        00:00:01 evolution-alarm
S  1000  5978  5977  0  76   0 11032  8410 poll   ?        00:00:00 evolution-alarm
S  1000  5979  5978  0  76   0 11032  8410 poll   ?        00:00:00 evolution-alarm
S  1000  5985  5967  0  76   0  6888  8308 poll   ?        00:00:00 evolution-data-
S  1000  5996     1  0  76   0 15964  8357 select ?        00:00:06 kscd
S  1000  5999     1  0  76   0 10220  6663 poll   ?        00:00:06 gnome-settings-
S  1000  6009     1  0  75   0  4140  1536 select ?        00:00:00 esd
S  1000  6011     1  0  75   0  2488  1668 select ?        00:00:01 xscreensaver
S  1000  6060  5881  0  75   0  7320 12268 rt_sig ? 00:00:02 xmms
S  1000  6061  6060  0  76   0  7320 12268 poll   ?        00:00:00 xmms
S  1000  6062  6061  0  75   0  7320 12268 select ?        00:00:00 xmms
S  1000  6063  6061  0  75   0  7320 12268 nanosl ?     00:00:00 xmms
S  1000  6064  6061  0  76   0  7320 12268 snd_pc ? 00:00:00 xmms
S  1000  6065  6061  0  75   0  7320 12268 nanosl ?     00:00:00 xmms
S  1000  6073  5881  4  75   0 12544  5637 select ?        00:00:11 Terminal
S  1000  6074  6073  0  85   0   788   698 unix_s ? 00:00:00 gnome-pty-helpe
S  1000  6075  6073  0  75   0  2024  1206 wait   pts/1    00:00:00 bash
R  1000  6086  6075  0  77   0   936   966 -      pts/1    00:00:00 ps

```

I want to learn what these things do and how they work! ;)

---

### Post by skoal on 2005-06-26
virgule, the first "issue" with the "-- MARK --" entries are logged by some system level daemon and can be safely ignored.  I really don't know which daemon or which service is populating that log file with it.  If you find out, let me know, but I read elsewhere it's not a problem.

I do not use evolution so I don't have an answer for you on that one either.  All those other services which are running can be safely stopped at your discretion.  Just:

sudo /etc/init.d/<service> stop

which ones you think you don't need.  There are some threads running around in these forums which might provide better insight as to what each one does.  Or just simply use the man pages for them.

Most of those services are running for a reason.  They provide *full* functionality for a whole host of services you will ever need or use while running Gnome (or Ubuntu).  I don't need most of them, so I stopped over 1/2 of them myself and setup my own custom init level (3 and 5) to boot from, not the default init level 2.

\\//_

---

### Post by skoal on 2005-06-26
Steveman, I re-read your original post and I see that you did try killing the "dbus-1" script with not effect.  I don't know what else to suggest, but that's what worked for me.  I think in my process of discovery to find out the same thing you did, I just pretty much kept "kill <PID>" until the drive access stopped.  Then I went back, tried to associate which service with what daemon I killed off, and eventually found the culprit.  I don't know which one is causing it for you.  As suggested by the first reply by "NotSoSuperUser", there may be other filesystem and/or hardware related drivers which may be causing it, not a service.  Trial and error is your best bet.

\\//_

---

### Post by mohaham on 2005-06-26
you might want to check this out...

change /etc/syslog.conf and reroute everything to /dev/tty8 instead of log files --> reduces disk activity and you can see stuff by pressing CTRL-ALT-F8

change /etc/hdparm.conf and add dma, 32bit, multisector and umask settings to your hard drive

change /etc/fstab and add noatime to all writeable media in the options section (ie. rw,user,noatime) These prevents your hard disk from writing access time on each file you read

hope this helps...

---

### Post by steveman on 2005-06-26
Thanks for the ideas.

Have modified the logging as recommended which is a good idea but no change.

Played around with hdparm a bit but apparently my drive doesn't support dma or unmask - maybe because it is SATA?

I did a bit more trial and error in terms of stopping services as well.  It seems that it is gnome related. The accesses don't occur before I log into GNOME.  Additionally, after stopping the gdm service, they seem to go away.  Not sure what useful conclusion to draw from this yet, but it's a start....

---

### Post by neighborlee on 2005-06-26
[QUOTE=steveman]Thanks for the ideas.

Have modified the logging as recommended which is a good idea but no change.

Played around with hdparm a bit but apparently my drive doesn't support dma or unmask - maybe because it is SATA?

I did a bit more trial and error in terms of stopping services as well.  It seems that it is gnome related. The accesses don't occur before I log into GNOME.  Additionally, after stopping the gdm service, they seem to go away.  Not sure what useful conclusion to draw from this yet, but it's a start....[/QUOTE]

not just gnome related..my laptop is playing with linspire atm which of course uses KDE..the access's are there and are about 3-5 seconds APart..

sorry to throw in wrench but it isn't just gnome..and frankly i'm not seeing this access in gnome here in ubuntu..

l8r
neighborlee

---

### Post by mrcbrown on 2005-06-26
[QUOTE=neighborlee]not just gnome related..my laptop is playing with linspire atm which of course uses KDE..the access's are there and are about 3-5 seconds APart..

sorry to throw in wrench but it isn't just gnome..and frankly i'm not seeing this access in gnome here in ubuntu..

l8r
neighborlee[/QUOTE]
 Do you have a firewall active on this system? I have one of my linux machines sitting in the DMZ so I can get access to the server while out and about, it's constantly getting scanned and login attempts - maybe try to put in APF or some basic iptables rules and limit ports the outside has access to - might help. You can always do a "netstat -a" and see who/what/where things are connected from.

---

### Post by steveman on 2005-06-27
Interesting....

As for mine, it's sitting behind a router on a home network so shouldn't be getting hit on any ports.

I tried a reinstall using ext2 rather than ext3 filesystem.  This seemed to improve the situation further, while not totally removing the problem either.  Strange stuff....

---

### Post by skoal on 2005-06-27
Steveman, are you sure you killed off the "hald" process and it still occurs?  I noticed on your prior post:

S 111 6724 1 0 76 0 6244 1922 - ? 00:00:00 hald

if shutting down a service doesn't kill it, just ps -A again, look for the PID of 'hald' and 'kill <PID>'.  I'm about a 100% sure that's what caused it for me.  The 'ole dbus/hal combo.

\\//_

---

### Post by neighborlee on 2005-06-28
[QUOTE=mrcbrown]Do you have a firewall active on this system? I have one of my linux machines sitting in the DMZ so I can get access to the server while out and about, it's constantly getting scanned and login attempts - maybe try to put in APF or some basic iptables rules and limit ports the outside has access to - might help. You can always do a "netstat -a" and see who/what/where things are connected from.[/QUOTE]

no firewall  except on linksys router but that hasn't changed and has been same in ubuntu where I get no access's at all..ohwell who knows with linspire frankly..sent ticket in but I have no heard anything back...just thought id let someone know it doesn't seem to be just gnome ..ive asked on linspire forums and no one seems to know whats going on 

cheers
neighborlee

---

### Post by kiddo on 2005-07-22
Sorry guys, I didn't read the whole thread (a bit too tired now, will try layer ;)) but I wanted to drop a note that I have the same problem, and someone else too, here's the bugzilla page

[https://bugzilla.ubuntu.com/show_bug.cgi?id=11596]("https://bugzilla.ubuntu.com/show_bug.cgi?id=11596")

Hopefully you could add your discoveries to that? I'd really like it if this was fixed in breezy, then I would *finally* enjoy a "dead silent" PC. Aaahh ^____^

Notes: this was since warty, now on two PCs running Hoary, one of those is a fresh Hoary and is a laptop. I am using ReiserFS, and it does not matter whether I am online or not, if I have specific programs open or not. I think, however, I once saw XCFE doing less noise than gnome. Not sure.

---

### Post by hatefulthreatening on 2006-02-15
I had a similair problem when I left a blank cd in my drive. Gnome or something would keep logging a stupid error message every three seconds. It was damned annoying when I was trying to sleep. I'm used to using the harddrive noise as an alert to tell me something is going on at my computer.

---

### Post by orbit on 2006-02-18
[QUOTE=skoal]Steveman, are you sure you killed off the "hald" process and it still occurs?  I noticed on your prior post:

S 111 6724 1 0 76 0 6244 1922 - ? 00:00:00 hald

if shutting down a service doesn't kill it, just ps -A again, look for the PID of 'hald' and 'kill <PID>'.  I'm about a 100% sure that's what caused it for me.  The 'ole dbus/hal combo.

\\//_[/QUOTE]

I had the same problem as the thread creator.  I killed hald and it fixed it!  Does anyone know what it does?  I read the man file, but there are not many details.  How will my system behave differently now that hald has been killed?


orbit

---

### Post by ericvmazzone on 2006-03-18
Would having a SMART hard drive cause it to run every 3-5 seconds?  

I've notice my Seagate doing this in Breazy and WinXP Pro.  I've only have this HD for about 1.5 months.  I don't want to fry this one too.

I've killed hald and it did not make any noticable difference.  Checking top there does not seem to be anything running to account for the disk access.

Using GtKrell I do not see any activity when this is going on, but the disk access light is on and I can sometimes here the disk running.

Under WinXP using google desktop with the system monitor plug-in I'm reading about 4-36kBps of activity for moments during the time the access light is on.

Any ideas?

I'm using reiserfs for boot root and home I have a 2G swap and NTFS for windows.  I am hardly using and of my RAM and nothing is displayed as being used in the swap spaces.  Windows is 30% full.  Root is I beleive 20% and home is 35% used.

Thanks.

---

### Post by mikeblaa on 2006-03-20
Crosspost from [http://www.ubuntuforums.org/showthread.php?p=845521](http://www.ubuntuforums.org/showthread.php?p=845521) as this thread seems more relevant.

I'm seeing consistent 28k writes every five seconds. When my computer first starts and before I login there is no activity. Once I'm in Gnome they begin. The most active processes I can see with top are:

gconfd-2
x-session-manager
gnome-cups-icon

When I examined the command line arguments used to start these processes, i saw this on gconfd-2 

# pstree -a | grep gconf
  |-gconfd-2 **5**
  |   |           |-grep gconf

Coincidence?

---

### Post by mikeblaa on 2006-03-20
[QUOTE=mikeblaa]Coincidence?[/QUOTE]

Yes. 

The culprit is in [CUPS]("https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/29895")

---

### Post by kiddo on 2006-03-20
Hmmm... I still have the disk seeks. I'm happy this is being investigated though. Isn't there any tool that could tell us what process used the disk? I'm pretty surprised.

I don't have the cups icon by the way (I killed it long ago). It even happens if I completely stop the CUPS service. Something else is the cause. 

Could this help at all? [http://tinyurl.com/m4nro](http://tinyurl.com/m4nro) (taken from [http://tinyurl.com/evlek](http://tinyurl.com/evlek), coming from [http://tinyurl.com/l4tjr](http://tinyurl.com/l4tjr))

---

### Post by marekm on 2006-09-11
Hi all.

The same problem (clicking every 5 sec.) in Dapper 6.06.1 with an old Seagate Baracuda disk but, solved by adding noatime option to fstab file... :)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               reiserfs notail,noatime          0       1
/dev/hda7       /media          ext3    defaults        0       2
/dev/hda5       /work           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


think, it helps you...

best regards 

Marek M.

---

### Post by kiddo on 2006-09-24
Hmm hi. I'm running edgy now, I added noatime and nodiratime to the fstab, that doesn't even solve it. I still get clicks every 10 seconds or so. Very annoying on a laptop. What the hell's going on >_<?

---

### Post by pwhite on 2006-09-27
You wouldn't happen to have beagled running would you? If so, try [Enabling_Extended_Attributes]("http://beagle-project.org/Enabling_Extended_Attributes") and modify /usr/bin/beagled so it doesn't start beagle in debug mode which enables "extensive logging". kjournald appears to sync every 5 seconds, which shouldn't be a problem if there's nothing to sync, but beagled in its standard configuration appears to always have something to write to disk since it's constantly reindexing and doing so verbosely.

Hope this helps,
Peter

---

### Post by kiddo on 2006-09-28
No, I don't have beagle, or tracker, and I even tried without tomboy, without gnome-cups-icon, without evolution-*.

---

