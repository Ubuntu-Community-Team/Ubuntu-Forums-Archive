---
title: "Add Programs To Startup.."
date: 2009-03-03
forum: General Help
---

### Post by Reaper29 on 2009-03-03
Im using Mint 6, but pretty sure its almost the same. Can someone please tell me how to add kpowersave to automaticly start when i start my laptop and boot up.

thanks in advance.

---

### Post by kevin11951 on 2009-03-03
> **Reaper29 said:**
> Im using Mint 6, but pretty sure its almost the same. Can someone please tell me how to add kpowersave to automaticly start when i start my laptop and boot up.

thanks in advance.

add it to /etc/init.d/rc.local...

(hint: the code in red, are the programs that run at start up, change them for your use)

is kpowersave a daemon?

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
	        [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		ES=$?
		[ "$VERBOSE" != no ] && log_end_msg $ES
		return $ES
	fi
}

case "$1" in
    start)
	do_start
	[COLOR="Red"]modprobe raw1394
	chown root /dev/raw1394[/COLOR]
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

---

### Post by Reaper29 on 2009-03-03
can you be alittle more specific as to how i do all this..lol...im new to linux..

how do i add it to /etc/init.d/rc.local ? and what am i suppose to add there?

---

### Post by kevin11951 on 2009-03-03
> **Reaper29 said:**
> can you be alittle more specific as to how i do all this..lol...im new to linux..

how do i add it to /etc/init.d/rc.local ? and what am i suppose to add there?

what is kpowersave, is it a gui program you interact with, or is it a background program that does stuff, but you dont actually use.

---

### Post by Reaper29 on 2009-03-03
> **kevin11951 said:**
> what is kpowersave, is it a gui program you interact with, or is it a background program that does stuff, but you dont actually use.

its a power program that i have to run everytime i startup the laptop.

---

### Post by kevin11951 on 2009-03-03
> **Reaper29 said:**
> its a power program that i have to run everytime i startup the laptop.

is it kde 4, or 3?

---

### Post by Reaper29 on 2009-03-03
> **kevin11951 said:**
> is it kde 4, or 3?

i have no idea..lol...i using mint 6 which is gnome, but i know its a program, where you can change all ur charge setting and diplay, cpu settings, etc... like the power management tool for ubuntu and mint. i just need the applet to start up for me, instead of me going to the start menu, then clicking on kpowersave.

---

### Post by mips on 2009-03-03
**[FONT=Tahoma][SIZE=2][COLOR=Red]Additionaly[/COLOR] you can use the powersave daemon to handle powermanagement if no user is logged in to the system ([http://sourceforge.net/projects/powersave/](http://sourceforge.net/projects/powersave/)).[/SIZE][/FONT]**

---

### Post by mips on 2009-03-03
Try this and see what it does,

Go to the following menu:
**System** -> **Preferences** -> **More Preferences** -> **Sessions**
 Click on **Startup Options** tab and click on Add button to add your program to startup.

But this will only run kpowersave when gnome is running.

---

### Post by Reaper29 on 2009-03-03
> **mips said:**
> Try this and see what it does,

Go to the following menu:
**System** -> **Preferences** -> **More Preferences** -> **Sessions**
 Click on **Startup Options** tab and click on Add button to add your program to startup.

But this will only run kpowersave when gnome is running.

thats exactly what i want, to add the kpowersave to run when gnome is running so i can see it on the task panel. i go to sessions like you said, i just dont know what the command is to put in the add panel.

---

### Post by mips on 2009-03-03
> **Reaper29 said:**
> thats exactly what i want, to add the kpowersave to run when gnome is running so i can see it on the task panel. i go to sessions like you said, i just dont know what the command is to put in the add panel.

How did you start it before, by clicking on a icon or typing the command in a terminal?
If it was an icon should be able to get the command form it's properties, if it was a terminal just use the same command you typed in.

---

### Post by Reaper29 on 2009-03-03
> **mips said:**
> How did you start it before, by clicking on a icon or typing the command in a terminal?
If it was an icon should be able to get the command form it's properties, if it was a terminal just use the same command you typed in.

it was by clicking on the icon, how do i find the properties?

---

### Post by mips on 2009-03-03
> **Reaper29 said:**
> it was by clicking on the icon, how do i find the properties?

No idea, I have not used gnome in years, maybe try right clicking on the icon?

---

### Post by Reaper29 on 2009-03-03
lol, ok no problem..

anyone else???

---

