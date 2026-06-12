---
title: "metacity start hangs after today's updates!"
date: 2006-08-04
forum: Desktop Environments
---

### Post by RikoW on 2006-08-04
Dear all,

I also have a problem login into gnome after today's update, which as far as I recall included a new kernel image, some gnome and cups stuff.

After I rebooted by computer, I was presented with the usual login screen. But after I typed in user and password, I only got a brown screen with a mouse pointer which could be moved but nothing else.

Turns out if you wait long enough (and I mean looonnngggg as in several minutes > 5) the window manager finally starts and everything seems to normal except that gkrellm doesn't run.

So, I found out, the login process hangs, when esd start. The process list when I get my brown screen looks like this:

```
 
> ps ax
  [...] 
 5260 tty6     Ss     0:00 /bin/login --
 5271 ?        Ss     0:00 x-session-manager
 5314 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 5317 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-ma 
 5318 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --
 5320 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 5
 5323 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 5325 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server -
 5327 ?        Sl     0:00 /usr/lib/control-center/gnome-settings-daemon --oaf-a
 5336 tty6     S+     0:00 -tcsh
>

```

after the window manager is up:

```

 5260 tty6     Ss     0:00 /bin/login --
 5271 ?        Ss     0:00 x-session-manager
 5314 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s 
 5317 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-ma
 5318 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 -- 
 5320 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2 5
 5323 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 5325 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server - 
 5327 ?        Sl     0:00 /usr/lib/control-center/gnome-settings-daemon --oaf-a
 [COLOR="Red"]5336 tty6     S+     0:00 -tcsh
 5351 ?        Ss     0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
 5358 ?        Ss     0:00 /usr/bin/metacity --sm-client-id=default0[/COLOR]
 5364 ?        Ss     0:01 gnome-panel --sm-client-id default1
 5366 ?        Ssl    0:01 nautilus --no-default-window --sm-client-id default2
 5369 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 5376 ?        Ss     0:00 update-notifier
 5378 ?        Rsl    0:00 gnome-terminal
 5386 ?        Ss     0:00 gnome-cups-icon --sm-client-id default3
 5388 ?        S      0:00 /bin/sh /usr/lib/openoffice/program/soffice -quicksta
 5402 ?        Ss     0:00 gnome-power-manager
 5406 ?        Sl     0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activat
 5420 ?        Sl     0:02 python /usr/lib/gdesklets/gdesklets-daemon
 5423 ?        Sl     0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid 
 5425 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 5426 ?        S      0:00 gnome-pty-helper
 5428 pts/0    Ss     0:00 -csh
 5441 ?        Rl     0:01 /usr/lib/openoffice/program/soffice.bin -quickstart -
 5451 ?        S      0:00 /usr/lib/tsclient/tsclient-applet --oaf-activate-iid= 
 5453 ?        S      0:00 /usr/lib/gnome-applets/cpufreq-applet --oaf-activate-
 5456 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i 5458 ?        S      0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=
 5466 pts/0    R+     >

```

Turning esd off in the Preferences -> Sound menu let's me login normally, however, it seems like metacity crashed when selecting certain menu items (for example the quit button). At least no menu or panel is working anymore.

I already reinstall everything through synaptic which has esd in its name, but didn't make a difference.

Any idea, what could be the problem.

---

### Post by RikoW on 2006-08-05
ok, all panic for nothing.

Seems like the problem is that esd does not like it, if the machine is restarted instead of shutdown and started (at least, that's what a post in some forum/newsgroup claims).
And indeed after stopping reboot cycles and in fact shutting my computer down and starting it again, everything was back to normal .... ](*,) 

Cheers,

             Riko

---

### Post by RikoW on 2006-08-10
Maybe I was to quick in claiming the problem went away by itself. Unfortunately, it still exists :(

When I login, the login process hangs before the gnome splash screen appears to show you what it is currently loading. This hanging persists for some minutes and finally continues.

When I turn esd off through the Preferences - Sound menu, the login process runs as normal but the 'Quit ...' button still causes to window manager not to respond anymore and logout is possible only via 'sudo shutdown -h now' :(

Maybe someone has an idea since some time passed after I posted the last time.

Thanks and cheers,

              Riko

---

### Post by vikrant82 on 2007-09-28
Man, I upgraded to gutsy today and am seeing same problem. Metacity kinds of hangs on certain menu items like "Quit". It takes like 30 seconds to respond... 

Did you find any particular reasons?

---

