---
title: "autostart.sh foesn´t seem to work"
date: 2011-02-25
forum: Desktop Environments
---

### Post by noneofthem on 2011-02-25
Hello everybody,

I just installed Ubuntu 10.10 using the minimal CD. I then installed Openbox and everything is working so far, except for tint2. I tried to put it into the autostart.sh in /home/noneofthem/.config/openbox, but it doesn´t exist there. Instead I found another version in /etc/xdg/openbox/. Changes to that version don´t seem to work either. Can anyone give me a hint on what I could try?

Thanks in advance!

noneofthem

---

### Post by aeiah on 2011-02-25
you should just be able to create the autoshart.sh file in ~/.config/openbox

it doesnt need any fancy formatting. just make it executible and put ```

tint2 &

```

---

### Post by ankspo71 on 2011-02-25
Hi,

Have you already tried adding the sleep command for tint2?

Instead of:
tint2 &

Try this:
(sleep 5s && tint2) &
or try this:
(sleep 5 && tint2) &

Info borrowed from:
[http://crunchbanglinux.org/wiki/howto/autostart_programs](http://crunchbanglinux.org/wiki/howto/autostart_programs)
[http://openbox.org/wiki/Help:Autostart](http://openbox.org/wiki/Help:Autostart)

Hope this helps

---

### Post by soad6 on 2011-02-25
not sure if this will help, but if you want your script to run at startup just add the script name to /etc/rc.local file with gedit.
add it before the exit(0).

---

### Post by noneofthem on 2011-02-25
Hello again!

Sorry, but I can´t seem to get it working. Here is what I have right now. Maybe you can see something I can´t.

/etc/rc.local
```
!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
~/.config/openbox/autostart.sh
exit 0
```

/home/noneofthem/.config/openbox/autostart.sh
```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
hsetroot ~/wallpaper.png &
xcompmgr -c -t-5 -l-5 -r4.2 -o.55 &

# SCIM support (for typing non-english characters)
export LC_CTYPE=ja_JP.utf8
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=scim
export QT_IM_MODULE=scim
scim -d &

# Programs that will run after Openbox has started
(sleep 4 && tint2) &
```

Please let me know if you need to see anything else. Thanks a lot!

---

### Post by Jose Catre-Vandis on 2011-02-25
If you are running openbox, you just don't need to put anything in rc.local.

Again, is autostart.sh executable?
```
sudo chmod +x ~/.config/openbox/autostart.sh
```

Remove all the cruft from your autostart.sh, you only need what you need (e.g. (sleep 4 && tint2) & )

Remove any blank lines or returns from autostart.sh as well, nothing below the last &  !!

Oh, and have you checked tint2 runs OK from a terminal? Might you need a full path?
```
:~$ /usr/bin/tint2 &
```

How are you starting openbox in the first place?

Normal way, boot to login command prompt, login, type startx, get blank screen with cursor, right click to see menu.

---

### Post by noneofthem on 2011-02-25
Hey!

I srart Openbox when logging in via xdm. The autostart.sh file was executable and no spaces or anything anywhere...

Anyway... Got bigger problems now. My monitor switches off just after grub. Must be my crappy Nvidia card. It has always been a pain in the neck. Time to remove it. Thanks everyone! Really appreciate your help today. Enjoy your weekend! :-)

---

### Post by urukrama on 2011-02-27
Make sure you start *openbox-session* and not just *openbox*. The latter only runs Openbox, the former runs the autostart.sh file first.

---

