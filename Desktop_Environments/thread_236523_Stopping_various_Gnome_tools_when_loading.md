---
title: "Stopping various Gnome tools when loading"
date: 2006-08-14
forum: Desktop Environments
---

### Post by harisund on 2006-08-14
Here's the output of my
ps axjf | tr -d '[0-9]?' | cut -d: -f2

```

 PPID   PID  PGID   SID TTY      TPGID STAT   UID   TIME COMMAND
 init
 migration/
 ksoftirqd/
 watchdog/
 events/
 khelper
 kthread
  \_ kblockd/
  \_ kacpid
  \_ kacpid-work-
  \_ kacpid-work-
  \_ pdflush
  \_ pdflush
  \_ aio/
  \_ kseriod
  \_ khubd
  \_ kacpid-work-
  \_ kacpid-work-
  \_ kacpid-work-
  \_ kacpid-work-
  \_ kacpid-work-
  \_ kacpid-work-
  \_ kacpid-work-
  \_ kacpid-work-
 kswapd
 khpsbpkt
 knodemgrd_
 kjournald
 /sbin/udevd --daemon
 shpchpd_event
 pccardd
 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 /usr/bin/dbus-daemon --system
 /usr/sbin/hald
  \_ hald-runner
      \_ /usr/lib/hal/hald-addon-acpi
      \_ /usr/lib/hal/hald-addon-keyboard
      \_ /usr/lib/hal/hald-addon-keyboard
      \_ /usr/lib/hal/hald-addon-keyboard
      \_ /usr/lib/hal/hald-addon-storage
      \_ /usr/lib/hal/hald-addon-storage
 /usr/sbin/powernowd -q
 /bin/login --
  \_ -bash
 dhclient eth
 dbus-daemon --fork --print-pid  --print-address  --session
 /usr/sbin/gdm
  \_ /usr/sbin/gdm
      \_ /usr/bin/X
      \_ x-session-manager
 dbus-daemon --fork --print-pid  --print-address  --session
 /usr/bin/dbus-launch --exit-with-session x-session-manager
 /usr/lib/libgconf-/gconfd-
 /usr/bin/gnome-keyring-daemon
 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=
 /usr/bin/esd -terminate -nobeeps -as  -spawnfd
 /usr/bin/metacity --sm-client-id=default
 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID
 gnome-panel --sm-client-id default
 nautilus --no-default-window --sm-client-id default
 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID
 /usr/lib/gnome-vfs-./gnome-vfs-daemon --oaf-activate-iid=OAFIID
 update-notifier
 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID
 gnome-volume-manager --sm-client-id default
 /usr/lib/gnome-applets/mixer_applet --oaf-activate-iid=OAFIID
 /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf-activate-iid=OAFIID
 gnome-power-manager
 /usr/lib/nautilus-cd-burner/mapping-daemon
 gnome-terminal
  \_ gnome-pty-helper
  \_ bash
      \_ ps axjf
      \_ tr -d -
      \_ cut -d
 gnome-screensaver

```

Now, where I can control what's running and what's not running? Here's what I particularly do not want running. Can Ubuntu or Gnome give me such fine grained control? 

(1)gdm
I do not want to run gdm. I want to login to console, and at the start of a command, I want to start the proper gnome session.
(2) /usr/bin/gnome-keyring-daemon
Nope. I don't mind entering passwords myself. Please DO NOT START A KEYRING DAEMON.
(3)/usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID
I don't know what this is, and if I do not know what it is, I want it KILLED
(4)nautilus --no-default-window --sm-client-id default
Isn't this the app responsible for showing me the desktop? Well, I want it not to anymore. Typically I either have Firefox, the terminal, Thunderbird or something open and I *NEVER* see my desktop. So please stop this guy from running.
(5)update-notifier
For heaven's sake, I switched from Windows to Linux so that I won't see the 'please update your system' taskbar notification. Big deal, in Widows that appears by default in the bottom right, in Ubuntu the same annoyance appears by default on top left. And when I install a new kernel, I will myself restart, thank you. I don't want Ubuntu constantly nagging me.
(6) gnome-volume-manager --sm-client-id default
Is this the guy who handles plugging in USB devices and stuff like that? How do I get rid of him? 
(7) /usr/lib/nautilus-cd-burner/mapping-daemon
WTF? I don't even have a CD burner. 


So can anyone tell me how I can stop these services? 

I know, I will probably receive replies like switch to a smaller/less heavy desktop environment. I will, thank you. I just want to fix Gnome along the way.

---

### Post by ardchoille on 2006-08-14
There is a very nice app in the repos, called sysv-rc-conf. I installed it and it allows you to tweak which services run at which runlevels. It's quite nice. It's in the universe repo. Enable universe and then: sudo apt-get install sysv-rc-conf

Once it is installed, open a term and type "sudo sysv-rc-conf" (without quotes) to start it. But, take care, this is very important stuff in there :). There are some commands along the top to help you out.

The gnome-settings-deamon is what tells gnome which themes to use for your gui apps. If you kill it, then all your gnome apps will look really ugly. If you don't mind everything looking like it's GTK1, then you can go ahead and kill gnome-settings-deamon. This is the app I start when I use other window managers so my gnome apps look good :)

Nautilus also manages the desktop (right-click menu, icons, etc) so if you kill all of the nautilus instances, you'll lose your dekstop too. Might wanna keep that one running if you like the dekstop wallpaper, desktop right-click menu, and icons :)

Update-notifier.. I'd always recommend to leave this running, unless you are good at remembering to update your system yourself.

gnome-volume-manager is the one which handles pluggable devices.

---

### Post by bkeithly on 2006-12-18
Gents

where did you find this fine ssh agent app?
I am looking for a way to get agent to start on boot and prompt me for my pass phrases before/after x starts.  Basically I want agent to be applied to all my terminal sessions.

---

