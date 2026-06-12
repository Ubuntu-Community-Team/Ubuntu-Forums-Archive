---
title: "ubuntu slow when not connected to internet"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Eremit on 2006-08-06
When my PC is not connected to the internet it takes a long time to start an application (doesn't matter what). The application itself than works at normal speed, it's just the startup process.

Any ideas? Maybe something with Gnome checking for an internet connection?

---

### Post by ciscosurfer on 2006-08-06
What apps are you trying to start?  Unless you are trying to update your system (install, upgrade, etc.), you shouldn't have any speed loss.  I've never encountered this issue.  Most (if not all) non-Internet programs never need access to the Web so I'm a little puzzled at your scenario.  Which programs specifically are you speaking of?

---

### Post by Eremit on 2006-08-06
For example: firefox, rhythmbox, evolution, nautilus, gnome terminal (all gnome applications)
They take up to 5 seconds to start!

I'll have to check out non-gnome appliactions.

I'm connected over LAN to a router(gateway). When the router is down(no internet access) startuptime of applications increases.

(I have deactivated update-notifier)

---

### Post by ciscosurfer on 2006-08-06
The first time you use an application after your computer has either been idle or off, will take longer than when you start it up again subsequent times.  I have a feeling that this is what going on.  Does this sound familiar: you try to start up a program, it takes longer than you expected, you disconnect from the Internet, you startup the program again and it loads quicker?   This has to do with caching and prefetch/preload, not with your connection to the Internet.

There is absolutely no correlation here between your being to connected to the Internet and your startup time.  I think you may be suffering from the placebo effect.

---

### Post by Eremit on 2006-08-07
> **ciscosurfer said:**
> The first time you use an application after your computer has either been idle or off, will take longer than when you start it up again subsequent times.  I have a feeling that this is what going on.  Does this sound familiar: you try to start up a program, it takes longer than you expected, you disconnect from the Internet, you startup the program again and it loads quicker?   This has to do with caching and prefetch/preload, not with your connection to the Internet.

There is absolutely no correlation here between your being to connected to the Internet and your startup time.  I think you may be suffering from the placebo effect.

No no no :-k

This effect is constant! Doesn't matter how often I open and close the same application. Logging in (gdm) also takes much more time without internet connection.
I know it sounds strange but that's the way it is!

Just plugged out my LAN cable.
Gnome-Terminal: 20 seconds
Mplayer(no gui): less than 1 second
Enemy Territory: 20 seconds
Nautilus: 20 seconds
Rhythmbox: 20 seconds
Bittorrent: less than 1 second
Gnome Calculator: 20 seconds
Blender: less than 1 second
Thunderbird: 15 seconds
PDF Viewer: 20 seconds

Cable back in:
everything back to normal

As you see some applications are not affected: blender, bittorent(python, no arch), mplayer(no gui)
I don't know when this started because most of the time I am connected to the internet.

](*,) ](*,) 

I will check what happens if I put the network interface down.

Maybe you can get something out of my running applications:
```

  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:01 init [2]
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S<     0:00 [events/0]
    6 ?        S<     0:00 [khelper]
    7 ?        S<     0:00 [kthread]
    9 ?        S<     0:00 [kblockd/0]
   10 ?        S<     0:00 [kacpid]
   95 ?        S      0:00 [pdflush]
   96 ?        S      0:00 [pdflush]
   98 ?        S<     0:00 [aio/0]
   97 ?        S      0:00 [kswapd0]
  686 ?        S<     0:00 [kseriod]
 1830 ?        S<     0:00 [khubd]
 1924 ?        S      0:00 [kjournald]
 2137 ?        S<s    0:00 /sbin/udevd --daemon
 2952 ?        S      0:00 [shpchpd_event]
 3051 ?        S<     0:00 [kgameportd]
 3478 ?        S      0:00 [kjournald]
 3834 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 3849 ?        Ss     0:00 /sbin/syslogd -u syslog
 3872 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 3874 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 3893 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 3908 ?        Ss     0:01 /usr/sbin/hald
 3909 ?        S      0:00 hald-runner
 3914 ?        S      0:00 /usr/lib/hal/hald-addon-acpi
 3964 ?        S      0:00 /usr/lib/hal/hald-addon-keyboard
 3974 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 3975 ?        S      0:00 /usr/lib/hal/hald-addon-storage
 3995 ?        Ss     0:00 /sbin/dhcdbd --system
 4012 ?        Ss     0:00 /usr/sbin/NetworkManager --pid-file=/var/run/NetworkM
 4030 ?        Ss     0:00 avahi-daemon: running [Terminal.local]
 4031 ?        Ss     0:00 avahi-daemon: chroot helper process
 4051 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file=/var/ru
 4292 ?        Ss     0:00 /usr/sbin/gdm
 4299 ?        S      0:00 /usr/sbin/gdm
 4304 tty7     SLs+   1:21 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut
 4408 ?        Ss     0:00 /usr/sbin/nmbd -D
 4410 ?        Ss     0:00 /usr/sbin/smbd -D
 4427 ?        S      0:00 /usr/sbin/smbd -D
 4499 ?        Ss     0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 4519 ?        Ss     0:00 /usr/sbin/atd
 4534 ?        Ss     0:00 /usr/sbin/cron
 4603 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4604 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4605 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4606 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4607 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 5274 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 5341 ?        Ss     0:00 x-session-manager
 5400 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 5403 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-ma
 5404 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --
 5406 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 5
 5409 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 5411 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5413 ?        Sl     0:01 /usr/lib/control-center/gnome-settings-daemon --oaf-a
 5418 ?        Ss     0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
 5420 ?        Ss     0:07 /usr/bin/metacity --sm-client-id=default0
 5425 ?        Ssl    0:12 gnome-panel --sm-client-id default1
 5427 ?        Ssl    0:06 nautilus --no-default-window --sm-client-id default2
 5430 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 5440 ?        Sl     0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activat
 5454 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 5457 ?        S      0:00 /usr/lib/quick-lounge-applet/quick-lounge-applet --oa
 5459 ?        Sl     0:00 /usr/lib/gnome-applets/drivemount_applet2 --oaf-activ
 5463 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 5467 ?        Sl     0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=
 5476 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.6 --oaf-ac
 5490 ?        Sl     0:00 /usr/lib/evolution/2.6/evolution-alarm-notify --oaf-a
 5512 ?        Ss     0:01 gnome-screensaver
 5533 ?        Sl     1:01 /usr/lib/firefox/firefox-bin -a firefox
 6266 ?        Rl     0:00 gnome-terminal --working-directory=
 6267 ?        S      0:00 gnome-pty-helper
 6268 pts/0    Ss     0:00 bash
 6289 pts/0    R+     0:00 ps ax

```

---

### Post by carontis on 2006-08-07
Hellò friend. I'm afraid something is hidden behind and you can't see it. Try this [http://www.wh-hms.uni-ulm.de/~mfcn/netspeed/]("http://www.wh-hms.uni-ulm.de/~mfcn/netspeed/")
and see if something is using your line. Usually on my pc when happened it was for something that toke the line (doesn't matter if it's ADSL or not). After that, you should also try to install RKHUNTER (see in Synaptic) and have a check to your pc.

Hope it helps!
Bye

---

### Post by ciscosurfer on 2006-08-07
Wow.  I've never heard of such a thing.  On a normal Ubuntu system, the correlation you've made above is non-existent.

Perhaps this is a hardware issue.  Perhaps you had a faulty install CD. Perhaps your system has been compromised.

---

### Post by fdoving on 2006-08-07
Check that your 'lo' interface is up. If it's not certain apps often become very slow.

Just my 0.2$

- Frode

---

### Post by Eremit on 2006-08-08
> **ciscosurfer said:**
> Wow.  I've never heard of such a thing.  On a normal Ubuntu system, the correlation you've made above is non-existent.

Perhaps this is a hardware issue.  Perhaps you had a faulty install CD. Perhaps your system has been compromised.

I upgraded from hoary and never had that issue before.

@carontis:
Thought about that too, but I never found something.

Today I tried "ifconfig eth0 down" and no problem with that. (Different to just plugging out the LAN cable)

Than I removed all kind of IPv6 stuff from /etc/hosts and now it seems the problem has disappeared. But I'll check that again before I believe it.

---

### Post by carontis on 2006-08-08
As "tempus fugit" I had time to answer only now... I'm working also if it is summer.
Weel, it happened to me long ago with Ubuntu 5.10 and I had lot to do before taking deicision to reformat my pc. After format it started normally and without problems. Can I know what ISP do you use? Is it one of the most known or is it from your country? It could depends from it too. Sometimes they don't say is their fault and the user goes crazy to find what is happening.

---

### Post by ciscosurfer on 2006-08-08
If it's not a security issue, you've got a bad install/upgrade.  Plain and simple.  On your list, Bittorrent, Thunderbird, and Firefox, are the only apps that legitimately access the Internet.

Back up your data, download and burn a fresh ISO, and reinstall.

---

### Post by Eremit on 2006-08-09
> **ciscosurfer said:**
> If it's not a security issue, you've got a bad install/upgrade.  Plain and simple.  On your list, Bittorrent, Thunderbird, and Firefox, are the only apps that legitimately access the Internet.

Back up your data, download and burn a fresh ISO, and reinstall.

Yeah probably I have, but: *oh there's a problem, let's reinstall everything* is the windows approach and I don't like that anymore. Besides I think dist-upgrades should be a clean thing in good distros.

To my problem: removing the IPv6 entries in the network config has solved the issue.

---

### Post by ciscosurfer on 2006-08-09
I'm glad everything is back to normal.  I will have to look into why your ipv6 entries were giving you trouble.  *grinning* I never doubted you (the experiences you were having), I had just never heard of such a thing before.  I'm interested to know why those problems occurred due to those entries...so if you find anything out, please let me know...and i will do the same :)

---

### Post by Eremit on 2006-08-10
> **ciscosurfer said:**
> I'm glad everything is back to normal.  I will have to look into why your ipv6 entries were giving you trouble.  *grinning* I never doubted you (the experiences you were having), I had just never heard of such a thing before.  I'm interested to know why those problems occurred due to those entries...so if you find anything out, please let me know...and i will do the same :)

unfortunately I just deleted them, but I think it were these:

```
# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 
```

Interesting:
[http://ubuntuforums.org/showthread.php?t=87479](http://ubuntuforums.org/showthread.php?t=87479)
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)
[http://notfaq.wordpress.com/2006/07/20/speed-up-firefox/#respond](http://notfaq.wordpress.com/2006/07/20/speed-up-firefox/#respond)

---

### Post by ciscosurfer on 2006-08-10
Those are interesting...

But this one ([http://ubuntuforums.org/showthread.php?t=87479](http://ubuntuforums.org/showthread.php?t=87479)) refers to an internet app...I do understand that disabling ipv6 lookups like this may increase the speed of the lookup...but again, it's an Internet app

This thread ([http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)) also refers to Internet apps...I have also seen this one and understand that responsiveness might improve as well in Firefox and Thunderbird b/c of disabling ipv6 lookups...

And this one too [http://notfaq.wordpress.com/2006/07/20/speed-up-firefox/#respond)]("http://notfaq.wordpress.com/2006/07/20/speed-up-firefox/#respond%29"), I have seen (seems like people are really having difficutlties with Linux messing up there lookups when ipv6 is enabled) -- only here, I don't have a modprobe.conf file, I have an aliases file in my /etc/modprobe.d/ directory...he's probably not using Ubuntu (maybe he is, but an older version).

Without question, ipv6 lookups seem to be an issue...however, I have yet to see any threads/posts/pages that refer to this being a problem with regular Gnome apps...I will continue looking and will keep you updated

In a couple of years, if not sooner, ipv6 will be completely universal, so most of these lookup issues will go away. ;)

---

### Post by ciscosurfer on 2006-08-10
I'm not sure if you [saw this or not]("http://ubuntuforums.org/showpost.php?p=478267&postcount=8"), but it attempts to explain these ipv6 lookup issues.

---

### Post by ciscosurfer on 2006-08-10
Additionally, [take a look at this thread]("http://ubuntuforums.org/showthread.php?p=478267")...read the entire thread b/c one answer may not work for you or may not be the best solution to your specific problem.

Also, it mentions stuff about bugs within programs.

---

### Post by ericbarch on 2006-10-28
I've had this same issue many times on different distros and I still don't know why it happens. Whenever my Internet goes down or the cable modem is unplugged, my computer running Ubuntu gets very sluggish. SSHing into it takes 20+ seconds just to get to the password prompt. Using SFTP the connection times out the first try. As soon as the Internet comes back or the cable modem is plugged back in, everything returns to normal. I don't really know what the problem is because my Windows machines still work fine. -Eric

---

### Post by Eremit on 2006-10-28
Hallo Eric,

finally someone to backup my "story" *g*
Have you tried to remove all IPv6 entries in the config files?
Interesting that you got the problem on different distros :|

---

### Post by ericbarch on 2006-10-28
Alright, I removed my IPv6 entries. Next chance I have to power down the Internet, I'll post what happens.

---

### Post by Nelson-Ray on 2006-12-12
Just letting you know that I seem to be having this problem. My internet connection went down today (right now I am using my laptop and smooching off my neighbors wifi) and one of my edgy computers slowed down to a crawl. Once the Ubuntu/Gnome splash screen comes on, it takes 2-3 minutes for it to go away. Opening terminal takes nearly a minute. NFS exports don't work either. I'm waiting for my internet to come back to see if my computer goes back to normal speeds. The strange thing is I have another Edgy computer that runs normally.

---

### Post by Nelson-Ray on 2006-12-12
Now that my internet connection is back, the computer that slowed down to a crawl when the internet was out, is now running normal/fast. Furthermore it can now export NFS mounts, whereas when the internet was down, the computer would not export NFS mounts on the local network.

Strange thing is this computer sits behind a router, same as another Ubuntu Edgy computer and only 1 computer exhibited this slow behavior when the internet was down.

---

### Post by deethree on 2006-12-12
I'll have to agree, my ubuntu install slowed to a crwal when my interent went down yesterday.

I was going to start a thread about this, kinda glad others have the same issue, hopefully it will be easier then getting flgrx working. :D

d3.

---

### Post by antw on 2006-12-18
I have seen the same slowdown in Ubuntu once I lost my connection 4 days ago. The computer was mostly unusable until I disabled the network connection. All apps would take up to 20sec+ to open, There was no excessive CPU usage just the computer sitting and waiting.

Once apps were open they would operate at normal speed.

---

### Post by LucidTaZ on 2006-12-18
I have this problem the other way around. Programs get slow when connected and act normally when unplugging the network cable. To see my thread and a list of programs I have tested it on, look here:
[http://www.ubuntuforums.com/showthread.php?t=317489](http://www.ubuntuforums.com/showthread.php?t=317489)

---

### Post by ricardo.caratti on 2006-12-25
I have the same problem in my notebook TOSHIBA Satellite M45-S331.
When a need to work without internet I have to turn off my wireless. 


> **Nelson-Ray said:**
> Now that my internet connection is back, the computer that slowed down to a crawl when the internet was out, is now running normal/fast. Furthermore it can now export NFS mounts, whereas when the internet was down, the computer would not export NFS mounts on the local network.

Strange thing is this computer sits behind a router, same as another Ubuntu Edgy computer and only 1 computer exhibited this slow behavior when the internet was down.

---

### Post by fernando-madrid on 2007-01-06
The same thing with TOSHIBA Tecra A-7 (Ubuntu 6.10)
Without LAN or Wireless toooo slowwwww

I don't have the problem with my desktop (Ubuntu 6.10) it works perfect with or without network, but the laptop bad, bad, bad ... :( 

Has anybody got an answer to this problem?

---

### Post by Eremit on 2007-01-07
> **Eremit said:**
> To my problem: removing the IPv6 entries in the network config has solved the issue.

Try that :-?

---

### Post by ISagalaev on 2007-01-18
Recently I've got this exact problem but today managed to find it and resolve it.

I've found out that on every GUI window start the x-session-manager (one of the components of GUI) does a DNS lookup for the name that is set as a Host name in System, Administration, Networking on the General tab. If you have a domain name set there then x-session-manager would look up for "Host.Domain".

 Normally when Ubuntu is installed this name is added to the local hosts table as an address 127.0.0.1 (Hosts tab in the Networking dialog) so it can be resolved without network connection (and in fact so it can be resolved at all). Accidentally I've managed to "clean up" this entry in Hosts some time ago and forgot it. This is why on each and every window opened Ubuntu was trying to ask the network about its own name :-). And slowed down by timeout when there were no network.

So in short:

- open System, Administration, Networking
- look for host name and domain name under General tab
- add "Host" and "Host.Domain" (if domain is not empty) as names for 127.0.0.1 under Hosts tab
- log out, then log in (i.e. restart x-session-manager for changes to take effect)

---

### Post by robdogg on 2007-02-02
Hey
same problem as everyone speed of opening up any program or terminal goes down when cable is out
tred  changing the name for 127.0.01 to "Host.Domain" no success

any other solutions


Thanks

---

### Post by Eremit on 2007-02-03
try removing the IPv6 entries in the network config files

---

### Post by quirt3 on 2007-02-03
It sounds like....a linux virus, but that's nigh impossible, thankfully.

---

### Post by jonathannonesuch on 2007-09-10
Thank you all very much for your contributions! What a relief to find out I am not the only one having this annoying problem...

Things got *very* slow on my Toshiba Satellite when I unplugged my internet connection (applications taking over 20 seconds to start up).

I think ISagalaev provides the right answer: the trouble lays in graphical user interface, because also the 'places' window and the 'help' window take an awful lot of time to open.

So I took his advice and nosed around in the System>Administration>Network window>Hosts Tab. And what did I see? There was the Localhost allright, 127.0.0.1 as it should be. But right under it was this host: "myname-laptop" with nr. 127.0.1.1. 

And then I remembered that the sluggishness problem started about the same time, a week ago, when I  had changed my hostname: the thing you see in front of the " $ " on the command line. I had changed it because I log in with username " myname " and I thought a command prompt like "myname@myname-laptop" does *not* look cool. So I changed the hostname to " themachine " (and when I look at the command line it now says "myname@themachine" which *does* look cool :))

So I changed this second host from "myname-laptop" to "themachine" (leaving the number 127.0.1.1 untouched), rebooted, and - presto! - problem solved...

Thank you all!
Jonathan Nonesuch

---

### Post by nichpakaich on 2008-04-01
just the steps I need .. it work for me

I also delete my workgrop entry (I ain't connected anyway, rite?) in additioni. And it runs like a dream :D

---

