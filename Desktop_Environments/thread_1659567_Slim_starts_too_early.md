---
title: "Slim starts too early"
date: 2011-01-04
forum: Desktop Environments
---

### Post by P.Kosunen on 2011-01-04
How can i set Slim display manager to start later (or load nvidia kernel module faster)?

```

sudo update-rc.d -f slim remove
sudo update-rc.d slim defaults 99

```

Tried to increase rc link number, but it didn't help. Slim tries to start 2 seconds before nvidia module gets loaded (Maverick minimal amd64).

---

### Post by cipherboy_loc on 2011-01-04
Doesn't Slim interface into GDM? In other words, if you go directly to the login page, won't it show up under the desktop environment menu? Fluxbox does, but I don't know how much Slim and Fluxbox differ.


Cipherboy

---

### Post by P.Kosunen on 2011-01-04
I use Slim to start Fluxbox with automatic login. Slim is display/login manager like GDM/KDM/XDM, i don't have GDM installed. "sudo /etc/init.d/slim start" after boot is finished (nvidia module loaded) works ok. SSD is too fast..

[http://slim.berlios.de/](http://slim.berlios.de/)

---

### Post by lykwydchykyn on 2011-01-04
Is slim being started via upstart or from sysv?  (you can tell by looking at /etc/init.d/slim -- if it's a symlink to /lib/init/upstart-job then it's being started by upstart).

I don't know the details on it, but if it's being started by upstart, then you can make it dependent on the video driver being loaded (I believe kdm and gdm are already set up this way).

If it's just a sysv init script, I'm not sure.  I know these scripts support dependencies, but how to actually specify the loading of the hardware drivers I don't know.

---

### Post by P.Kosunen on 2011-01-04
It is sysv script. Have to check if i can convert it to upstart.

---

### Post by P.Kosunen on 2011-01-05
Changing to upstart fixed it.

/etc/init/slim.conf (modded from kdm.conf):
```

# SLiM - Simple Login Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description     "Simple Login Manager"
author          "Richard Johnson"  

start on (filesystem
          and started dbus
          and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on runlevel [016]

emits starting-dm

env XORGCONFIG=/etc/X11/xorg.conf

script
    if [ -n "$UPSTART_EVENTS" ]
    then
    [ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/bin/slim" ] || { stop; exit 0; }

    # Check kernel command-line for inhibitors
    for ARG in $(cat /proc/cmdline)
    do
        case "${ARG}" in
        text|-s|s|S|single)
                    plymouth quit || :  # We have the ball here
            exit 0
            ;;
        esac
    done
    fi

    if [ -r /etc/default/locale ]; then
    . /etc/default/locale
    export LANG LANGUAGE
    elif [ -r /etc/environment ]; then
    . /etc/environment
    export LANG LANGUAGE
    fi
    export XORGCONFIG

    exec slim
end script

```

```

sudo update-rc.d -f slim remove
sudo mv /etc/init.d/slim ~/backup/slim-original-sysvrc-script
sudo ln -s /lib/init/upstart-job /etc/init.d/slim

```

---

### Post by lykwydchykyn on 2011-01-06
Very nice; you should submit this as a patch to Ubuntu's SLiM maintainer.

---

### Post by P.Kosunen on 2011-01-07
Ok, i created bug report with fix info.

---

### Post by abelthorne on 2011-10-16
Hello,
I have a somewhat similar problem.

I'm trying to build a custom Ubuntu install based on Openbox, using Slim as a login manager. I had the problem that Plymouth anim kept playing (although shrinked) on Slim screen and on Openbox background. I noticed that plymouth was still running in the processes list (although I didn't know if it was normal or not). After some research, I found a bug report ([https://bugs.launchpad.net/ubuntu/+source/slim/+bug/567120](https://bugs.launchpad.net/ubuntu/+source/slim/+bug/567120)) saying that there was a problem in Slim, that used init instead of upstart, thus Plymouth didn't know it had to stop, etc.

I then found this thread. I've applied the modifications to convert Slim to an upstart job (as far as I understand it). After rebooting, the Plymouth animation isn't displayed anymore on Slim screen (hurray!) but after I enter my login+pwd, I end up on the Plymouth screen that seems to be stuck and Openbox doesn't start (not-so-hurray).

I managed to revert to the original situation. Any idea what doesn't work in my case? What can I check? Mabe the fix isn't adapted anymore to the current Ubuntu version (using Oneiric)?

---

### Post by proycon on 2013-03-17
It seems this issue is still relevant in Ubuntu 12.10 , in addition to the fix P.Kosunen mentioned I also had to edit /etc/init/plymouth-stop.conf  and add slim there, otherwise plymouth would keep running after slim has been started.

---

### Post by wildmanne39 on 2013-03-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

