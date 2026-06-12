---
title: "Press a button to disable gdm from loading on boot?"
date: 2009-06-15
forum: Desktop Environments
---

### Post by capitales7 on 2009-06-15
Hi all.

I want to be able to press/hold down a key when ubuntu is starting up, which then stops gdm from loading, so that ubuntu loads in cli.
So far, I've come up with modifying the gdm init.d script to do a read on a specific key, which then does an exit on the rest of the script.

I haven't tried this yet... my linux-fu isn't that strong yet and I don't wanna fudge everything up.

1) Has anyone done this intelligently before?
2) Is the solution above doable and safe?

Any help is appreciated! :)

Cheers.

---

### Post by zika on 2009-06-15
> **capitales7 said:**
> Hi all.

I want to be able to press/hold down a key when ubuntu is starting up, which then stops gdm from loading, so that ubuntu loads in cli.
So far, I've come up with modifying the gdm init.d script to do a read on a specific key, which then does an exit on the rest of the script.

I haven't tried this yet... my linux-fu isn't that strong yet and I don't wanna fudge everything up.

1) Has anyone done this intelligently before?
2) Is the solution above doable and safe?

Any help is appreciated! :)

Cheers.You already have that. Be sure that You do not have auto-log-on turned ON. (Administration->LoginWindow->Security) Then, while computer is waiting for Your user-name and password press Alt-Ctrl-F1 and You are in CLI. Press Alt-Ctrl-F7 and You are back to log-in screen ...

---

### Post by capitales7 on 2009-06-15
> **zika said:**
> You already have that. Be sure that You do not have auto-log-on turned ON. (Administration->LoginWindow->Security) Then, while computer is waiting for Your user-name and password press Alt-Ctrl-F1 and You are in CLI. Press Alt-Ctrl-F7 and You are back to log-in screen ...

Yes there is that! But the reason I wanted to do this is to not have gnome eat up system resources when I want to leave my server running and only connect to it remotely.
I guess that's a decent solution though :)

---

### Post by zika on 2009-06-15
Remove gdm from the boot with **sysv-rc-conf** or through **Administration->Services** and start it in CLI when You need it with ```
(sudo) /etc/init.d/gdm start
(sudo) startx
```if I remember it correctly, I've done it some time ago. Nevertheles, it is easy to do it ...

---

### Post by capitales7 on 2009-06-15
> **zika said:**
> Remove gdm from the boot with **sysv-rc-conf** or through **Administration->Services** and start it in CLI when You need it with ```
(sudo) /etc/init.d/gdm start
(sudo) startx
```if I remember it correctly, I've done it some time ago. Nevertheles, it is easy to do it ...

lol. I'm being annoying now, but I want it to normally start gdm, but sometimes I want to start in cli.

---

### Post by leniviy on 2009-07-12
Hi. I wanted the same, so I did it for Archlinux. You can try it on your distro.
1) create file /etc/rc.d/functions.d/read_timeout or /etc/init.d/functions.d/read_timeout
or whatever functions.d dir you have or just append it to the "functions" file :
```

#!/bin/sh

#/etc/rc.d/functions.d/read_timeout

read_timeout_getch ()     # gets one char from kbd, no "Enter" necessary
{
    OLD_STTY=`stty -g`
    stty cbreak -echo
    GETCH=`dd if=/dev/tty bs=1 count=1 2>/dev/null`
    stty $OLD_STTY
}


read_timeout()
{
 # try to echo 1 line or 1 char from stdin within given time
 # usage: read_timeout number [-ch]
 TTY=
 if ((echo "">/dev/null)>/dev/tty) 2>/dev/null; then
  TTY="/dev/tty"
 else
  TTY=`tty`
 fi

 if [ ! -z "$TTY" -a "$2" = "-ch" ]; then
  READCMD='REPLY=`dd if="'"$TTY"'" bs=1 count=1 2>/dev/null`'
  OLD_STTY="`stty -g`"
  stty cbreak -echo
 else
  READCMD='read REPLY'
 fi
 (sh -c '
  (sleep "$1"; kill $$ 2>/dev/null)& BG=$! \
  && '"$READCMD"' && echo "$REPLY" \
  && kill -INT $BG \
  && for PID in `ps --ppid $BG -o pid=`; do \
   kill $PID; \
   done \
  && kill $BG \
  ' _dummy_ "$1"
  echo this line guarantees expression in parentheses has its own pid >/dev/null
 ) 2>/dev/null
 if [ "$2" = "-ch" ]; then
  stty "$OLD_STTY"
 fi
}

```2) run the following command in your terminal for testing (again, replace /etc/rc.d/functions with the actual path to "functions" file )

```

. /etc/rc.d/functions
echo "press Y to not start gnome";REPLY=`read_timeout 5 -ch` && if [ "$REPLY" = "y" -o "$REPLY" = "Y" ]; then echo "not starting gnome"; exit 1; fi

```it should exit now if you press "Y" within 5 seconds

3) insert the second line from above into /etc/rc.d/gdm like this:
```

case "$1" in
  start)
    echo "press Y to not start gnome";REPLY=`read_timeout 5 -ch` && if [ "$REPLY" = "y" -o "$REPLY" = "Y" ]; then echo "not starting gnome"; exit 1; fi
    stat_busy "Starting GDM"
    /usr/sbin/gdm

```test it: /etc/rc.d/gdm start
switch to text terminal and try there, finally, reboot and try at boot time

P.S. upgrades can replace modified "gdm" file, consider creating a wrapper script and launch it instead of gdm.

---

