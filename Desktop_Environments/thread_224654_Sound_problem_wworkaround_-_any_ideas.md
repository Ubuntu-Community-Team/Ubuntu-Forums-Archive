---
title: "Sound problem w/workaround - any ideas?"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Apostata on 2006-07-28
Hey folks,

  I recently upgraded my m'board (Biostar 6100-939, onboard Realtek sound chip) and I found that - particularly for True Combat Elite (yes, it's a game), there's no sound. I did some research and found that if I ran the following commands:

 [COLOR=#000000][FONT=Tahoma]sudo chown user /proc/asound/card0/pcm0p/oss[/FONT][/COLOR] 
[COLOR=#000000][FONT=Tahoma]
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss[/FONT][/COLOR]

 One thing I'd like to know is how I can run these two commands at startup (or better still, if someone has a better fix!). FYI - the first command, changing the ownership of [COLOR=#000000][FONT=Tahoma]/proc/asound/card0/pcm0p/oss[/FONT][/COLOR] - it's really strange, because after reboot the ownership reverts back to root.

  Cheers for any assistance,

  Matt

---

### Post by FenrisAbraxas on 2006-07-28
> **Apostata said:**
> Hey folks,

  I recently upgraded my m'board (Biostar 6100-939, onboard Realtek sound chip) and I found that - particularly for True Combat Elite (yes, it's a game), there's no sound. I did some research and found that if I ran the following commands:

 [COLOR=#000000][FONT=Tahoma]sudo chown user /proc/asound/card0/pcm0p/oss[/FONT][/COLOR] 
[COLOR=#000000][FONT=Tahoma]
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss[/FONT][/COLOR]

 One thing I'd like to know is how I can run these two commands at startup (or better still, if someone has a better fix!). FYI - the first command, changing the ownership of [COLOR=#000000][FONT=Tahoma]/proc/asound/card0/pcm0p/oss[/FONT][/COLOR] - it's really strange, because after reboot the ownership reverts back to root.

  Cheers for any assistance,

  Matt

In /etc/init.d/ there should be a "something.local" edit that file and add the line to load at startup, no need to change the ownership

---

### Post by Apostata on 2006-07-28
Cool - I'll give that a try. Thanks!

---

### Post by CarlesOriol on 2006-07-28
Great!

Thanks

It helped me in other problem!!!

---

### Post by Apostata on 2006-07-29
Two questions:

  In /etc/init.d/rc.local (the script you mention), does it make any difference where I put the command? I notice the script ends with 'esac' - does it need to end with this?

  Lastly, /etc/init.d/rc.local directly references /etc/rc.local. When I opened the second file, it looks like a more appropriate place to put the command. It says:

[FONT="Arial"]# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0[/FONT]

Would it best if I used this one, vs. the one in init.d?

Cheers,

Matt

---

### Post by Apostata on 2006-08-07
Follow-up - I put the command in /etc/init.d/rc.local and it seems to work fine - thanks FenrisAbraxas for the suggestion.

---

### Post by chainsaw on 2006-12-31
Hey Guys, 

I've been messin around with linux for a few months now, so I have a *general* idea of how things work. Now to my problem:

I'm building a HTPC using ubuntu and I also have a biostar geforce 6100 and I can't seem to get my sound to work. using the  onboard. I was under the impression that it should have worked from the box without having to install any drivers (realtek, nforce, etc.) so I'm not sure what to attribute my problem to. 

Say I tried the same suggestion as posted here, that is, adding the commands to etc/init.d/rc.local, where in the file to I add those two lines?

If it is any help my rc.local looks like this:

#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
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

Any help would be appreciated, as an HTPC without any sound is pretty lame!

Thanks,
Tom

---

