---
title: "why is nautilus so slow?"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Mouldy_19 on 2005-12-05
one of the most basic things i want in an OS is a filebrowser with instant response, on a comp 3ghz with 1024mb of ram thats not too much to ask is it?
explorer opens as soon as i click on it in windowsxp but nautilus sometimes takes 10 seconds to open, so any help on an instant open for nautlius would be appreciated.

---

### Post by ScreemingBlue on 2005-12-05
I agree, Nautilus is Veeeery slow with the same spec PC. Try using XFE, not as pretty but much faster.

---

### Post by megamania on 2005-12-05
Nautilus *is* slow, but 10 seconds to open is a lot.

I have an Athlon 2100 processor (if I remember correctly) with 512mb ram and it opens in around two seconds, I would say. I can time it when I'm back home, if you're interested, but I'm pretty sure it's nowhere near to ten seconds...

---

### Post by earobinson on 2005-12-05
my guess is somethigns wrong, it should be much faster than this.
can you post a.

ps -awx

are you running a lot of extra programs?

---

### Post by Mouldy_19 on 2005-12-05
> Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:01 init [2]
    2 ?        SN     0:00 [ksoftirqd/0]
    3 ?        S<     0:00 [events/0]
    4 ?        S<     0:00 [khelper]
    5 ?        S<     0:00 [kthread]
    7 ?        S<     0:00 [kacpid]
  102 ?        S<     0:00 [kblockd/0]
  133 ?        S      0:00 [pdflush]
  134 ?        S      0:00 [pdflush]
  136 ?        S<     0:00 [aio/0]
  135 ?        S      0:00 [kswapd0]
  721 ?        S      0:00 [kseriod]
 1921 ?        S      0:00 [khubd]
 3086 ?        S      0:00 [kjournald]
 3216 ?        S<s    0:00 udevd --daemon
 4401 ?        S      0:00 [khpsbpkt]
 4946 ?        S      0:00 [kjournald]
 5774 ?        S      0:00 [pccardd]
 5830 ?        S      0:00 [knodemgrd_0]
 6627 ?        Ss     0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0
 6923 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 6938 ?        Ss     0:00 /sbin/syslogd -u syslog
 6955 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 6957 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 6970 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 6983 ?        Ss     0:01 /usr/sbin/hald
 6988 ?        S      0:00 hald-addon-acpi
 7001 ?        S      0:00 hald-addon-storage
 7381 ?        Ss     0:00 /usr/sbin/gdm
 7386 ?        S      0:00 /usr/sbin/gdm
 7450 ?        SL     0:14 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 7460 ?        Ss     0:01 /usr/sbin/cupsd -F
 7720 ?        Ss     0:00 /sbin/cardmgr
 7839 ?        Ss     0:00 /usr/sbin/nmbd -D
 7841 ?        Ss     0:00 /usr/sbin/smbd -D
 7854 ?        Ss     0:00 hcid: processing events
 7860 ?        Ss     0:00 /usr/sbin/sdpd
 7870 ?        S<     0:00 [krfcommd]
 7879 ?        S      0:00 /usr/sbin/smbd -D
 7907 ?        Ss     0:00 /usr/sbin/atd
 7920 ?        Ss     0:00 /usr/sbin/cron
 7963 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 7964 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 7965 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 7966 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 7967 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 7968 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 7991 ?        Ss     0:00 x-session-manager
 8029 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
 8032 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
 8033 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
 8035 ?        S      0:01 /usr/lib/gconf2/gconfd-2 5
 8065 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 8067 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
 8069 ?        S      0:00 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd
 8075 ?        S      0:00 /usr/lib/gamin/gam_server
 8087 ?        S      0:00 xscreensaver -nosplash
 8111 ?        Ss     0:01 /usr/bin/metacity --sm-client-id=default0
 8116 ?        Ssl    0:01 gnome-panel --sm-client-id default1
 8118 ?        Ssl    0:02 nautilus --no-default-window --sm-client-id default2
 8120 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 8126 ?        Ss     0:00 update-notifier --sm-client-id default7
 8128 ?        Ssl    0:00 firestarter --start-hidden
 8130 ?        Ss     0:00 gnome-cups-icon --sm-client-id default3
 8132 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 8135 ?        S      0:00 /usr/lib/gconf2/gconfd-2 12
 8255 ?        S      0:01 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=31
 8258 ?        Sl     0:00 /usr/lib/gnome-vfs2/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=34
 8264 ?        Sl     0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd
 8273 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 8280 ?        S      0:00 /usr/lib/gnome-applets/battstat-applet-2 --oaf-activate-iid=OAFIID:GNOME_BattstatApplet_Factory --oaf-ior
 8282 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=40
 8284 ?        R      0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=41
 8287 ?        S      0:00 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf-activate-iid=OAFIID:GNOME_NetstatusApplet_Factory -
 8289 ?        S      0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Fact
 8509 ?        S      0:00 /bin/sh /usr/bin/firefox
 8520 ?        S      0:00 /bin/sh /opt/firefox/run-mozilla.sh /opt/firefox/firefox-bin
 8525 ?        Sl     1:45 /opt/firefox/firefox-bin
 8562 ?        S      0:05 gaim
 8722 ?        Sl     0:00 gnome-terminal --working-directory=/home/mike
 8724 ?        S      0:00 gnome-pty-helper
 8725 pts/0    Ss     0:00 bash
 8735 pts/0    R+     0:00 ps -awx


the only programs i have running are gaim firefox and firestarter
its not always 10 seconds just every now and again, but its always at least 4-5 seconds which isnt acceptable after about 5 seconds i double click again only for 2 windows to open a few seconds later. there must be a way to get it to open instantly even if it means running nautilus in the background hidden.

---

### Post by Kray on 2005-12-05
Nautilus in many aspects is more advanced than Windows Explorer, eg:
- thumbnailing abilities (for many image formats, pdf etc)
- mime type discovery in Windows is based on file extension, in Gnome file content is often checked, too - change extension in some PNG file, Nautilus will still know that this is image file...
- few other things, don't remember now, some time ago I read post on Gnome mailinglist about it... memora fragilis... lol...

That said - yes, Nautilus is slow. But my overall experience is that more heavyweight Linux DE like KDE or Gnome are slower than Windows (and other aspects like dynamic lib linking doesn't make it any better ;-)). And before u call me Windoze troll (;-)) - I have installed many Linux distrubutions in past 10 years, each time ending with quote "Not yet".

IIRC next Gnome stable version (2.14) should brings some (serious, I hope) performance improvements. This is really needed...

---

### Post by earobinson on 2005-12-05
Ah you could turn off all the thumbnailing and counting, that would speed it up.

Also are you axcessing a local drive or network drive, how big is the drive how much are you using, how fast is the drive?

---

### Post by pmj on 2005-12-05
This has also been my experience with Nautilus. Straight after boot it opens in less than a second, a few hours later it takes about 1-3 seconds and when the system has been up for a couple of days it can sometimes take up to 10 seconds to open, and I have no idea why that is because I always have plenty of CPU and more than 100MB RAM left.

And it's just not opening Nautilus. Opening folders in the same Nautilus window can take so long that you get a message asking you if you want to abort. If you just let it run, though, Nautilus will eventually wake up and open the folder. Is it the same for you?

That said, things got much better for me after I upgraded to Breezy. Nautilus is still slow, but nowhere near as slow as it was on Hoary.

---

### Post by Mouldy_19 on 2005-12-06
the drive is 80GB 7200rpm hitachi deskstar and its local, 55GB used
> - mime type discovery in Windows is based on file extension, in Gnome file content is often checked, too - change extension in some PNG file, Nautilus will still know that this is image file...
yeah id guessed that must be a part of it.

---

### Post by hollowhead on 2005-12-06
nautilus isn't slow on my system which is a lower spec than some above but the help file is.  Also it crashes all the time.

---

### Post by bunty on 2005-12-06
[QUOTE=Mouldy_19]the drive is 80GB 7200rpm hitachi deskstar and its local, 55GB used

yeah id guessed that must be a part of it.[/QUOTE]

Nautilus is slow. One of the best things about windows WAS explorer on 95/98. Sadly it got worse.

Despite the large number of file managers written for linux I dont see anything as simple , quick and efficient to use.

XFE is probably the closest for simple file management.

If you are working with images I would suggest using an image browser. I find pornview quite good (yes it really is called that, there's patch I wrote on gentoo forums if you want to rebuild it with a more sensible name).

HTH

---

