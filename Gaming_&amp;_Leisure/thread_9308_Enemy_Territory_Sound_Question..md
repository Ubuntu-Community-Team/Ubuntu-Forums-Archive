---
title: "Enemy Territory Sound Question."
date: 2004-12-27
forum: Gaming &amp; Leisure
---

### Post by RU63 on 2004-12-27
Heya, 

I have been hooked on ET since downloading and installing it last week.  But, I am a little annoyed that i have write,
 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

in root terminal to make the sound work everytime i restart my comp.  Is there a way to load that command during computer startup?

Thanks

---

### Post by ploum on 2004-12-27
Put the command in a file (with #!/bin/sh  on the first line).
Put this file in /etc/init.d/   (check that it has execution rights)

---

### Post by RU63 on 2004-12-27
[QUOTE=ploum]Put the command in a file (with #!/bin/sh  on the first line).
Put this file in /etc/init.d/   (check that it has execution rights)[/QUOTE]
 1. So, I make a new file, maybe called "ETsound"  -  
2. then write on the first line: #!/bin/sh
3. then write on the next line: echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
4. then save it
5. then move the file to the directory : /etc/init.d

???

---

### Post by RU63 on 2004-12-28
[QUOTE=RU63]1. So, I make a new file, maybe called "ETsound"  -  
2. then write on the first line: #!/bin/sh
3. then write on the next line: echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
4. then save it
5. then move the file to the directory : /etc/init.d

???[/QUOTE]
 I did the abouve and it didn't work

---

### Post by banadushi on 2004-12-28
Close, but your not telling it to startup anywhere.

1st of all, I would reccomend that you copy /etc/init.d/skeleton to /etc/init.d/etsound or the like.

Then edit it so you have the appropriate stat/stop sections.

You will then need to link it into your runlevels, where to want it to start.  Something line `ln -s /etc/rc2.d/S99etsound /etc/init.d/etsound` will work.  You could also use `update-rc.d` see the man page for syntax.

Note, I have a general startup script written that will work for multiple binaries.  When I get to work and fire up my laptop, I'll post it here too.

Rock on!

Jason

---

### Post by banadushi on 2004-12-28
Here is my starup script.  You can edit the GAME variable to be a space separated list of game binaries.

```

#!/bin/sh

set -e

. /lib/lsb/init-functions
. /etc/default/rcS

case $1 in
  start|restart|reload|force-reload)
    ;;
  stop)
    exit 0
    ;;
  *)
    log_success_msg "Usage: $0 {stop|start|restart|reload|force-reload}"
    exit 1
    ;;
esac

log_begin_msg "Setting alsa-game parameters..."

GAMES="et.x86"

for GAME in $GAMES
do
    if [[ `echo "$GAME 0 0 direct" > /proc/asound/card0/pcm0p/oss` ]]
    then
        log_warning_msg "Setting parameter for $GAME failed."
    fi
done

log_end_msg 0

```

---

### Post by RU63 on 2005-01-03
"You can edit the GAME variable to be a space separated list of game binaries. "

Does this mean that wherever i see the CAPS i edit that variable?

I do not fully understand.  This is in a new realm for me.  I have copied your binary script exactly as my etsound file.  But nothing has worked.  I think you want me to do some things with the skeleton but I am not sure what to do after I copy it to my etsound.  Can you show me an example of what u did.  I am learning so much!!!  Linux is great!

Thankyou

---

### Post by RU63 on 2005-01-03
"You can edit the GAME variable to be a space separated list of game binaries. "

Does this mean that wherever i see the CAPS i edit that variavle?

I do not fully understand.  This is in a new realm for me.  I have copied your binary script exaclty as my etsound file.  But nothing has worked.  I think you want me to do some things with the skeleton but I am not sure what to do after I copy it to my etsound.  Can you show me an example of what u did.  I am learning so much!!!  Linux is great!

Thankyou

---

### Post by banadushi on 2005-01-03
Yea you can add another game binary into the GAME variable, so if you also had wolfenstein on the box and wanted it to work as well you would put:
```

GAMES = "et.x86 wolf.x86"

```
Technically its not a binary, just a script.  So you have the file /etc/init.d/etsound?  If so you need to make it executatble with:
```

chmod +x /etc/init.d/etsound

```
This will allow you to manually start it by calling it  `/etc/init.d/etsound start`.  If you want it to do it's thing automatically on boot then you need to link it into a runlevel.  You can use update-rc.d to do this (see the man page), or just symlink it where you want it to startup.  Mine is as such:
```

ln -s /etc/init.d/etsound /etc/rc2.d/S13etsound

```
I am assuming that also is still set at /etc/rc2.d/S12alsa, so it will only load after alsa has loaded.

Have fun

Jason

---

