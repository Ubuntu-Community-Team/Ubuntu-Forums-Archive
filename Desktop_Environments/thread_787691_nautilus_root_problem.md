---
title: "nautilus root problem"
date: 2008-05-09
forum: Desktop Environments
---

### Post by obis666 on 2008-05-09
Hi, I installed the latest version of Ubuntu the day it was released and I am having nautilus problems (I think). I ran 2 instances of this command at once (2 terminals):
>sudo nautilus

I did this to simplify copying some sound files from my download dir to my /usr/share/sounds/ dir. I have never had a problem doing this in the past but in this latest version it messes up Gnome. Everything ran fine until I rebooted and then it just hangs trying to load gnome. I checked the permissions of the files I moved. The files are owned by root and have the proper permissions. I even removed the files I placed in the /usr/share/sounds dir. The exact same problem has happened on 2 different machines now (the second machine I didnt move any files I just opened >sudo nautilus and browsed around and then x'ed out.) I can run XFCE on the second machine but I have not tried on the original. Any suggestions would be greatly appreciated. I have finals this week and I really don't have much time to figure this out (or reinstall for that matter). Thanks in advance.

---

### Post by hermes0710 on 2008-05-09
If it's not such a big trouble, try removing the nautilus settings from your users directory. Else than that, try adding a new user and log in as the new user. Does this still happen?

---

### Post by logos34 on 2008-05-09
try

**gksudo** nautilus

---

### Post by obis666 on 2008-05-11
ok first thanks for the ideas. I created a new user with no problems I was able to start gnome with nothing abnormal happeneing. but looking at my old profile I have a directory with weird permissions listed (or rather nothing listed.) So I did a ls -al in my old dir and I got 

-rw-r--r--  1 obis666 obis666    249 2008-05-11 13:54 .gtk-bookmarks
d?????????  ? ?       ?           ?                 ? .gvfs
-rw-------  1 obis666 obis666   3464 2008-05-11 13:56 .ICEauthority

yes the question marks are there. I didnt fill them in. 

so I did a 
>sudo bash 
and then:
>chown -R obis666 .gvfs 
and got:
>chown: cannot access `.gvfs': Permission denied

then I did a:
>chmod 700 .gvfs
and got:
>chmod: cannot access `.gvfs': Permission denied



any ideas?

---

### Post by obis666 on 2008-05-12
ok, after logging out of the new profile has the same result. It just hangs on startup. this occurs over and over, create a new profile from failsafe term, reboot, then the profile no longer works. any help please?

---

### Post by hermes0710 on 2008-05-12
It seems that logging in creates settings for a specific process which is not able to auto start again based on them. I suggest you firstly disable compiz and if that was not the problem go to System>Administration>Services and start playing with the services (disable one by one to see which one causes the problem)

---

### Post by obis666 on 2008-05-12
I've already tried turning off compiz. This is not the problem. I also un-checked the various services from the admin menu. I dont think this is the problem because I ran ubuntu 8.04 for about 2 weeks with no problems at all until tried to
>sudo nautilus
and then I started having problems. I didnt make any changes to the system before the issues started other than running nautilus as root.

---

### Post by hermes0710 on 2008-05-13
Try removing all settings from nautilus (it's a folder under home directory but i don't know which exactly, i am not home)

---

### Post by obis666 on 2008-05-13
I tried this already, I moved everything in my home directory into a thumbdrive and restarted (leaving no config files at all). This allows me to start gnome just fine, however... When I reboot or logout then the problem reoccurs. Gnome just hangs indefinitely.

---

### Post by Awalton on 2008-05-14
Reasons like this are why I cannot profess enough:

[b]Using Nautilus as Root is UNSUPPORTED, UNTESTED, AND DANGEROUS.
DO NOT RUN NAUTILUS AS ROOT, EVEN FOR "SIMPLE, HARMLESS TASKS".[/b] 
(blinking red text would have been better...)

*ahem*. Now that we have that out of the way: what part of GNOME is locking up? Does everything else still work if you kill Nautilus (nautilus -q, killall nautilus, etc)? If the problem is persisting across users then it's probably a bit more serious...

---

### Post by obis666 on 2008-05-14
> **Awalton said:**
> what part of GNOME is locking up? Does everything else still work if you kill Nautilus (nautilus -q, killall nautilus, etc)? If the problem is persisting across users then it's probably a bit more serious...

When I log into Gnome normally or with a failsafe Gnome, it just hangs, sometimes the desktop image and the panels show up, but none of the menu's work. Nothing works, I cannot bring up a terminal, nautilus, or any applications within gnome. All that I have is a an image and non-working panels. And yes the problem exists for all users. I create a new user and the user functions normally for one session (until logout) and then the same problem.

> **Awalton said:**
> [b]Using Nautilus as Root is UNSUPPORTED, UNTESTED, AND DANGEROUS.
DO NOT RUN NAUTILUS AS ROOT, EVEN FOR "SIMPLE, HARMLESS TASKS".[/b] 
(blinking red text would have been better...)


I'm not really sure where this message originated, but I have never seen this before in my life. If I had ever seen something like this before, I assure you I would not have posted anything here (Its not as if I knew it was a risk and went ahead and did it anyway), I would have first: not have done it in the first place, and second: I would have known that the problem I am having is what goes along with using something unsupported. This is not the case here, I am one to use manuals and follow them. However, I have used >sudo nautilus countless times, in at least 25 distro's and never once had a problem like this before. 

Also just to be clear, does your cautionary statement include using gksudo? (suggested earlier by logos34)

---

### Post by Awalton on 2008-05-14
> **obis666 said:**
> 
I'm not really sure where this message originated, but I have never seen this before in my life.

You have now. Remember it, and remember it well. (Maybe I should fly it in my signature or something...) Nautilus was not designed to run as the root user, it does all kinds of I/O on all kinds of files at its own will, and isn't well tuned to not touch or modify files it shouldn't (normally it's jailed by permissions to know which files not to touch, but when you're running as root, you're giving Nautilus permission to run amok). Running Nautilus as root should be considered as harmful as running as root all of the time. And we know how glamorous Windows makes that look...

> **obis666 said:**
> However, I have used >sudo nautilus countless times, in at least 25 distro's and never once had a problem like this before. 

Metaphorically, "I've had unprotected sex dozens of times, this is my first time catching an STD!" It's no different.

> **obis666 said:**
> Also just to be clear, does your cautionary statement include using gksudo? (suggested earlier by logos34)
It includes every possible way of escalating Nautilus' permissions, including gksudo. The correct way would be to integrate something like PolicyKit into Nautilus with very fine grained privileges for these kinds of tasks, with explicit permission and confirmation for each task, but no such additions have been made as of yet. But for now, be smart: Use the smallest possible hammer to fix problems, don't drag out the wrecking ball to tap in a few nails.

> **obis666 said:**
> When I log into Gnome normally or with a failsafe Gnome, it just hangs, sometimes the desktop image and the panels show up, but none of the menu's work. Nothing works, I cannot bring up a terminal, nautilus, or any applications within gnome. All that I have is a an image and non-working panels. And yes the problem exists for all users. I create a new user and the user functions normally for one session (until logout) and then the same problem.

As per this problem, can you check the permissions and ownership on the files that you added to /usr/share/sounds? You'll probably want to verify permissions and ownership of other files as well... It's weird to me that it would function for one log-in and then break when you log out, though. When you log in for the first time, are their any gnome-related processes running as root? Can you try clearing out all of your session's temporary files and assure the permissions on all of the other files?

Also, to change permissions on the .gvfs mount point, kill any and all running instances of gvfs processes including the fuse daemon, then do so. GVFS processes are started on demand, so this should be fine. But it shouldn't matter though, I don't think gvfs-fuse not being able to mount would cause such a hang (maybe it's a bug?) And it shouldn't matter at all if you don't have gvfs-fuse installed... 

Once you've done all of this and restarted and confirmed its still a problem, you should check to see what's actually hanging. Go out to a VT and grab a list of processes (ps aux at least) and come back to us. We'll need a lot more info to diagnose this one. It could be as simple as bad permissions on a temporary file that we can't write to and need to in order to start certain processes, to an install-destroying badly thumbnailed text configuration file that could take ages to discover (yes, Nautilus thumbnails text files too, but that's only a small part of the reason Nautilus should never be ran as root)...

---

### Post by oneferna on 2008-05-14
It's always about sex with you guys, isn't it? If you don't know how to fix the problem, just move along.

I know nautilus developers and have been using nautilus since about 2001. We've certainly run it was root. You should run it with gksudo though.

Please post the output of:
ps -aux 

To copy and paste it easier you can:
ps -aux > output_ps   
and then open it with your favorite text editor and copy and paste here.

---

### Post by Awalton on 2008-05-14
> **oneferna said:**
> It's always about sex with you guys, isn't it? If you don't know how to fix the problem, just move along.

I don't have enough information to fix the problem, and requested it in my last post (which you seem to have reiterated). And giving a metaphor as to why abhorrent behavior should **NOT, UNDER ANY CIRCUMSTANCES BE REINFORCED** is deemed helpful in most universes. Sigh, c'est la vie. Maybe someday people will listen to advice instead of, well, breaking their systems.

> I know nautilus developers and have been using nautilus since about 2001.
Funny that. I **am** a [Nautilus developer](http://svn.gnome.org/viewvc/nautilus/trunk/ChangeLog?revision=14162&view=markup), GIO and GVFS developer (feel free to look up the changelogs on those too). Let me say this again: Nautilus is not safe to be ran as root, period. Same goes for the vast majority of programs like it (spawning tons of processes, doing untold I/O on files that it normally doesn't have permission to even read, etc). If it breaks your system, you can keep all of the pieces. I know for a fact the code I've written inside of GVFS shouldn't be ran as root, and as Nautilus spawns gvfsd, and gvfsd spawns gvfs-network... well you get my point.

If this is indeed Nautilus' fault and not something else going on (bad permissions on a file is currently top of the list), the whole issue would have been avoided by using mv. It's a lesson to be learned.

---

### Post by obis666 on 2008-05-21
Sorry its been a week or something, I have been busy and it takes forever to go through all the steps to make a working profile. Anyway... I had to create a 6th profile and here is what I got from the ps aux:



USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2844  1688 ?        Ss   01:42   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   01:42   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   01:42   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   01:42   0:01 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   01:42   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   01:42   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   01:42   0:00 [khelper]
root        42  0.0  0.0      0     0 ?        S<   01:42   0:00 [kblockd/0]
root        45  0.0  0.0      0     0 ?        S<   01:42   0:00 [kacpid]
root        46  0.0  0.0      0     0 ?        S<   01:42   0:00 [kacpi_notify]
root       120  0.0  0.0      0     0 ?        S<   01:42   0:00 [kseriod]
root       154  0.0  0.0      0     0 ?        S    01:42   0:00 [pdflush]
root       156  0.0  0.0      0     0 ?        S<   01:42   0:02 [kswapd0]
root       197  0.0  0.0      0     0 ?        S<   01:42   0:00 [aio/0]
root      1462  0.0  0.0      0     0 ?        S<   01:42   0:00 [ksuspend_usbd]
root      1465  0.0  0.0      0     0 ?        S<   01:42   0:00 [khubd]
root      1498  0.0  0.0      0     0 ?        S<   01:42   0:00 [ata/0]
root      1505  0.0  0.0      0     0 ?        S<   01:42   0:00 [ata_aux]
root      2126  0.0  0.0      0     0 ?        S<   01:42   0:00 [scsi_eh_0]
root      2128  0.0  0.0      0     0 ?        S<   01:42   0:00 [scsi_eh_1]
root      2446  0.0  0.0      0     0 ?        S<   01:42   0:00 [kjournald]
root      2649  0.0  0.0   2520  1040 ?        S<s  01:42   0:00 /sbin/udevd --daemon
root      2975  0.0  0.0      0     0 ?        S<   01:42   0:00 [ipw2200/0]
root      2980  0.0  0.0      0     0 ?        S<   01:42   0:00 [kpsmoused]
root      3857  0.0  0.0      0     0 ?        S<   01:42   0:00 [pccardd]
root      4388  0.0  0.0   1716   512 tty4     Ss+  01:42   0:00 /sbin/getty 38400 tty4
root      4389  0.0  0.0   1716   512 tty5     Ss+  01:42   0:00 /sbin/getty 38400 tty5
root      4393  0.0  0.0   1716   508 tty2     Ss+  01:42   0:00 /sbin/getty 38400 tty2
root      4394  0.0  0.0   1716   512 tty3     Ss+  01:42   0:00 /sbin/getty 38400 tty3
root      4396  0.0  0.0   1716   508 tty6     Ss+  01:42   0:00 /sbin/getty 38400 tty6
root      4571  0.0  0.0   2456  1352 ?        Ss   01:42   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4616  0.3  0.0      0     0 ?        S<   01:42   0:09 [kondemand/0]
syslog    4679  0.0  0.0   1936   688 ?        Ss   01:42   0:00 /sbin/syslogd -u syslog
root      4731  0.0  0.0   1872   536 ?        S    01:42   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4734  0.0  0.1   3300  2128 ?        Ss   01:42   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       4756  0.1  0.0   2964  1460 ?        Ss   01:42   0:02 /usr/bin/dbus-daemon --system
root      4773  0.0  0.1  21212  2268 ?        Ssl  01:42   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      4787  0.0  0.0   3536  1316 ?        Ss   01:42   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4800  0.0  0.1   4476  2196 ?        Ss   01:42   0:00 /usr/bin/system-tools-backends
root      4829  0.0  0.0   5312   988 ?        Ss   01:42   0:00 /usr/sbin/sshd
avahi     4850  0.0  0.0   2760  1412 ?        Ss   01:42   0:00 avahi-daemon: running [old-profile-lappie.local]
avahi     4851  0.0  0.0   2760   464 ?        Ss   01:42   0:00 avahi-daemon: chroot helper
root      4891  0.0  0.1   6040  2516 ?        Ss   01:42   0:00 /usr/sbin/cupsd
root      4941  0.0  0.0   6524  1372 ?        Ss   01:42   0:00 /usr/sbin/nmbd -D
root      4943  0.0  0.1  10112  2744 ?        Ss   01:42   0:00 /usr/sbin/smbd -D
root      4981  0.0  0.0   2020   904 ?        Ss   01:42   0:00 /usr/sbin/dhcdbd --system
root      5000  0.0  0.0  10112  1068 ?        S    01:42   0:00 /usr/sbin/smbd -D
111       5001  0.0  0.2   6296  4372 ?        Ss   01:42   0:02 /usr/sbin/hald
root      5004  0.0  0.1   7884  2368 ?        Ssl  01:42   0:00 /usr/sbin/console-kit-daemon
root      5066  0.0  0.0   3352  1176 ?        S    01:42   0:00 hald-runner
root      5079  0.0  0.0   3416  1156 ?        S    01:42   0:00 hald-addon-input: Listening on /dev/input/event6 /dev/input/event7 /dev/input/event1 /dev/input/event3 /dev/input/event4 /dev/input/event5
root      5098  0.0  0.0   3428  1236 ?        S    01:42   0:00 /usr/lib/hal/hald-addon-cpufreq
111       5099  0.0  0.0   2204   904 ?        S    01:42   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5113  0.0  0.0   3420  1156 ?        S    01:42   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5159  0.0  0.0   3172  1260 ?        Ss   01:42   0:00 /usr/sbin/hcid -x -s
root      5165  0.0  0.0      0     0 ?        S<   01:42   0:00 [btaddconn]
root      5166  0.0  0.0      0     0 ?        S<   01:42   0:00 [btdelconn]
root      5175  0.0  0.0   3020  1116 ?        S    01:42   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5179  0.0  0.0   3084  1308 ?        S    01:42   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5182  0.0  0.0      0     0 ?        S<   01:42   0:00 [krfcommd]
root      5242  0.0  0.0  14060  1656 ?        Ss   01:42   0:00 /usr/sbin/gdm
dhcp      5256  0.0  0.0   2440  1188 ?        S    01:42   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
daemon    5295  0.0  0.0   1984   424 ?        Ss   01:42   0:00 /usr/sbin/atd
root      5311  0.0  0.0   2104   892 ?        Ss   01:42   0:00 /usr/sbin/cron
root      5423  0.0  0.0   1716   508 tty1     Ss+  01:42   0:00 /sbin/getty 38400 tty1
old-profile    5754  0.0  0.2   5992  4160 ?        SN   01:48   0:00 /usr/lib/libgconf2-4/gconfd-2 4
old-profile    5832  0.0  0.0   2700  1064 ?        Ss   01:48   0:00 dbus-daemon --fork --print-address 24 --print-pid 26 --session
old-profile    5841  0.0  0.1   5184  3596 ?        SL   01:48   0:00 esd -nobeeps
old-profile    5861  0.0  0.9  39648 18652 ?        S    01:48   0:00 gnome-panel --sm-client-id default1
old-profile    5869  0.0  0.1  31904  3180 ?        Ssl  01:48   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
old-profile    5890  0.0  0.1   5372  2080 ?        S    01:48   0:00 /usr/lib/gvfs/gvfsd
old-profile    5900  0.0  0.0  29048  1876 ?        Ssl  01:48   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/old-profile/.gvfs
old-profile    5946  0.0  0.5  30616 10388 ?        SNl  01:48   0:00 trackerd
old-profile    6006  0.0  0.1  22168  2672 ?        S    01:48   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.4 /org/gtk/gvfs/exec_spaw/0
old-profile    6016  0.0  0.6  29472 12464 ?        S    01:48   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=23
root      6334  0.0  0.2  18464  4296 ?        S    01:53   0:00 /usr/sbin/gdm
root      6337  1.5  1.1  38744 23004 tty7     Ss+  01:53   0:32 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
new-profile   6382  0.0  0.2   7268  4332 ?        S    01:53   0:00 /usr/lib/libgconf2-4/gconfd-2 13
new-profile   6385  0.0  0.0  14340  2052 ?        S    01:53   0:00 /usr/bin/gnome-keyring-daemon -d --login
new-profile   6389  0.0  0.3  28860  7508 ?        Ssl  01:53   0:00 /usr/bin/gnome-session
new-profile   6503  0.0  0.3  22916  6572 ?        Ss   01:53   0:00 /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
new-profile   6507  0.0  0.0   2700  1076 ?        Ss   01:53   0:00 dbus-daemon --fork --print-address 24 --print-pid 26 --session
new-profile   6510  0.0  0.4  39852 10064 ?        Sl   01:53   0:01 gnome-settings-daemon
new-profile   6531  0.0  0.1   5372  2084 ?        S    01:53   0:00 /usr/lib/gvfs/gvfsd
new-profile   6539  0.2  1.0  41336 22460 ?        S    01:53   0:04 gnome-panel --sm-client-id default1
new-profile   6542  4.9  2.6 120588 55524 ?        Sl   01:53   1:46 nautilus --no-default-window --sm-client-id default2
new-profile   6545  0.0  0.1  15216  2628 ?        Ss   01:53   0:02 gnome-screensaver
new-profile   6553  0.0  0.1  31904  3176 ?        Ssl  01:53   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
new-profile   6609  0.0  0.1  22164  2668 ?        S    01:53   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.3 /org/gtk/gvfs/exec_spaw/0
new-profile   6610  0.0  0.2  14608  5728 ?        S    01:53   0:00 bluetooth-applet --singleton
new-profile   6618  0.0  0.5  26916 10872 ?        S    01:53   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=19
new-profile   6625  0.0  0.2  15220  5516 ?        S    01:53   0:00 tracker-applet
new-profile   6628  0.0  0.4  28644  9556 ?        Sl   01:53   0:00 /usr/lib/evolution/2.22/evolution-alarm-notify
new-profile   6632  0.0  0.5  31640 10416 ?        SNl  01:53   0:00 trackerd
new-profile   6635  0.0  0.5  31100 12372 ?        S    01:53   0:01 nm-applet --sm-disable
new-profile   6636  0.0  0.5  24268 12176 ?        S    01:53   0:00 python /usr/share/system-config-printer/applet.py
new-profile   6638  0.0  0.4  23456  8636 ?        Ss   01:53   0:00 gnome-power-manager
new-profile   6639  0.0  0.2  20668  4700 ?        Ss   01:53   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
new-profile   6692  0.0  0.7  47824 15128 ?        Sl   01:53   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=23
new-profile   6696  0.0  0.6  29236 13260 ?        S    01:53   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=26
new-profile   6703  0.0  0.0   1772   480 ?        Ss   01:53   0:00 /bin/sh -c /usr/bin/compiz-decorator
new-profile   6704  0.0  0.0   1772   508 ?        S    01:53   0:00 /bin/sh /usr/bin/compiz-decorator
new-profile   6706  0.0  0.4  18328  9708 ?        S    01:53   0:00 /usr/bin/gtk-window-decorator
new-profile   6738  0.2  0.5  20776 12236 ?        S    01:54   0:05 metacity --replace
root      6751  0.0  0.5  13136 11200 ?        S    01:54   0:00 /usr/bin/perl /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
root      6949  0.0  0.0      0     0 ?        S<   01:56   0:00 [scsi_eh_2]
root      6951  0.0  0.0      0     0 ?        S<   01:56   0:01 [usb-storage]
new-profile   7109  0.1  0.9  69304 19660 ?        Sl   01:58   0:02 gnome-terminal
new-profile   7111  0.0  0.0   2912   860 ?        S    01:58   0:00 gnome-pty-helper
new-profile   7112  0.0  0.0   4604  1956 pts/0    Ss   01:58   0:00 bash
root      7129  0.0  0.0   4104  1720 pts/0    S+   01:58   0:00 bash
root      8288  0.0  0.0      0     0 ?        S    02:14   0:00 [pdflush]
new-profile   8314  4.4  4.3 214276 90756 ?        Sl   02:14   0:38 /usr/lib/firefox-3.0b5/firefox
new-profile   8468  0.0  0.0   4624  2008 pts/1    Ss   02:17   0:00 bash
new-profile   8613  0.4  0.9  34184 18656 ?        S    02:20   0:02 gedit file:///home/new-profile/output_ps
new-profile   8976  0.0  0.0   2644  1004 pts/1    R+   02:29   0:00 ps aux


I really am just about ready to just re-install, but I dont want to have the same issues again so I'de like to figure out what I'm doing wrong so I dont run into the same problems. I really need to run linux I hate booting into windows (blah). Thanks in advance.

---

### Post by obis666 on 2008-05-21
Anyone have any ideas before I end this session and install something else? I'de really prefer not to re-install, but I cant do anything with the system the way it is.

---

### Post by fmonjaraz on 2008-05-21
I keep getting this error message "Nautilus cannot handle computer: locations", I can't get into my external hardrive or zip disks.  Any hints???

---

### Post by obis666 on 2008-05-21
I also have had this problem with the latest Ubuntu. I have no idea why its happening but it is easily mounted from terminal. Other than that I dont know what to tell you.

---

### Post by fmonjaraz on 2008-05-22
how do you do that??

---

### Post by obis666 on 2008-05-22
first identify the drive you want to mount with:
sudo fdisk -l

you should get back something like this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         510     4096543+  1b  Hidden W95 FAT32
/dev/sda2   *         511        6303    46532272+   c  W95 FAT32 (LBA)
/dev/sda3            6304       16827    84534030    7  HPFS/NTFS
/dev/sda4           16828       19457    21125475    5  Extended
/dev/sda5           16828       17313     3903763+  82  Linux swap / Solaris
/dev/sda6           17314       19457    17221648+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf5fe0b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488386552+   b  W95 FAT32

usually the external drive or zip disk is in a separate group, for me my external drive is  /dev/sdb1 , I can tell because I know the drive is 500gb and it is FAT32

now go to you media directory with:
cd /media

then create the directory you want to mount the device under:
sudo mkdir external

you can name it anything but I usually name it whatever the drive is already labeled as

then mount the device with:
sudo mount /dev/sdb1 /media/external

if your drive is ntfs just add:
sudo mount -t ntfs /dev/sdb1 /media/external

the t is for type (I think), if its something else like mac or fat32 you just have to identify the type of drive.

I know it seems like a lot if you have never done this before (No offense but I assume you haven't done this before) but after you've done it a few times its not to hard. Hope that helps.

---

### Post by obis666 on 2008-05-22
other than that, does anyone have any suggestions for my inability to keep a persistently usable profile using Gnome? I really cant wait much longer.

---

### Post by fmonjaraz on 2008-05-22
Thanks a lot!!!! The "External" file now even comes out in "Places".  Thank you very much!!! I hope I don't have to do this every time that I want to look at my external drive.

---

### Post by obis666 on 2008-05-22
This latest version of Ubuntu works very randomly in this aspect. I have it installed on 3 machines. One machine it mounts hard disks properly and automatically every time, one machine never mounts anything, and the third mounts randomly. I cant tell you why, probably just one of those kinks they have not totally worked out. I know someone that has never gotten Ubuntu to auto mount her hard drives with any version. It seems like if it likes your machine it works and if it does not, well then you might wanna right some shell scripts to simplify your life,.. at least thats what I've done.

---

