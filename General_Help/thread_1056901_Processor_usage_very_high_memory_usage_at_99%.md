---
title: "Processor usage very high memory usage at 99%"
date: 2009-02-01
forum: General Help
---

### Post by amwhitaker on 2009-02-01
I run the 64 bit version. A few days ago, when i turned on my computer, the processor started reading at being at 50% when nothing was running. When I would run other programs it would increase to around 90% or higher, my memory usage starts out around 50% but as my session gets longer it rises to 99%. Any ideas?

 PID TTY      STAT   TIME COMMAND
 5648 ?        Ssl    0:00 x-session-manager
 5730 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 5733 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pul
 5735 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 6 --print-addres
 5788 ?        Ssl    0:02 /usr/bin/pulseaudio -D --log-target=syslog
 5800 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 5802 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
 5809 ?        Ss     0:00 /usr/bin/seahorse-agent --execute x-session-manager
 5812 ?        S      0:00 /usr/lib/gvfs/gvfsd
 5813 ?        S      0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-w
 5820 ?        Ssl    0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 5821 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 5823 ?        S      0:00 /bin/sh /usr/bin/compiz
 5828 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/andy/.gvfs
 5891 ?        SL     0:06 /usr/bin/compiz.real --ignore-desktop-hints --replace
 5900 ?        Ss     0:00 gnome-screensaver
 5901 ?        Ss     0:00 /bin/sh -c /usr/bin/compiz-decorator
 5902 ?        S      0:00 /bin/sh /usr/bin/compiz-decorator
 5904 ?        S      0:00 /usr/bin/gtk-window-decorator
 5905 ?        S      0:02 gnome-panel
 5906 ?        S      0:00 nautilus --no-desktop --browser
 5909 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5916 ?        S      0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
 5918 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 5921 ?        S      0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 5924 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvf
 5927 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs
 5932 ?        S      0:01 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activ
 5937 ?        Sl     0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
 5939 ?        S      0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-app
 5948 ?        SNl    0:00 trackerd
 5949 ?        Sl     0:00 /usr/lib/evolution/2.24/evolution-alarm-notify
 5953 ?        S      0:00 bluetooth-applet
 5954 ?        S      0:00 update-notifier
 5955 ?        S      0:00 tracker-applet
 5958 ?        S      0:00 python /usr/share/system-config-printer/applet.py
 5963 ?        S      0:00 nm-applet --sm-disable
 5964 ?        Ss     0:00 gnome-power-manager
 5971 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-2.24 --oaf-a
 5982 ?        Sl     0:00 /usr/lib/evolution/2.24/evolution-exchange-storage --
 6021 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 6050 ?        S      0:01 pidgin
 6259 ?        Sl     0:00 gnome-terminal
 6261 ?        S      0:00 gnome-pty-helper
 6262 pts/0    Ss     0:00 bash
 6279 pts/0    R+     0:00 ps -x

---

### Post by Hobgoblin on 2009-02-01
The **top** command will show you what is using the most CPU.

---

### Post by grashdur on 2009-02-26
I have a very similar situation from time to time: Processor use (as shown in the System Monitor which I have on my top toolbar) suddenly goes up to 100% while I'm not doing anything at all. The computer gets loud, like it's working hard. When I click the System Monitor icon, I see that two processes are working together to use up the processor's capacity: mixer_applet2 and gnome-system-monitor. When I stop the mixer_applet2 process, processor use goes back down to around zero. The mixer_applet2 seems to be the busier of the two. I haven't tried stopping the other one, as it sounds like something too essential to go without. Processor use also returns to normal if I reboot.

This same thing happens both on my Gateway desktop computer with Hardy Heron, and on my Sony Vaio laptop with Intrepid Ibex. Not every day, just every so often. And this doesn't seem to impact performance: As soon as I start working with a program, these two processes make way for them and don't seem to slow things down.

So I'm just curious: My processor is at 100%, for no reason that I can fathom. Is this okay? What is it working so hard to do? Is it defragmenting? Or doing some sort of diagnostics?

---

