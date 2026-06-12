---
title: "Lightweight login manager"
date: 2007-07-22
forum: Desktop Environments
---

### Post by mefoo on 2007-07-22
I'm usually a lurker but I can't find a direct answer to this problem so here it goes:

I did a server installation of feisty for a low end system and I am looking to setup a lightweight login/display manager. I've set my sight on [SLiM]("http://slim.berlios.de") and found a prepackaged deb which I have installed. At this point I need directions on having SLiM start at boot time so I don't have to login at the commandline and use startx.

As far as I can understand I need to create a init script and put it where? TIA.

---

### Post by louistan3 on 2007-07-22
im no expert...

but dont you just place a sym link of the init script in one of the /etc/rc* directories?

not sure which one is the startup.... but i believe its rc2

duno if this is what youre looking for but hope this helps :)

---

### Post by mefoo on 2007-07-23
Ok so I placed the sample init script from the slim website into /etc/init.d/ and made this file executable. Following your advice I then made a simlink of this file and placed it into /etc/rc2.d. But no go.

Maybe the init script needs tweaking? Here it is:
```

#!/bin/sh
#
# /etc/rc.d/slim: start/stop slim
#

case $1 in
start)
	/usr/bin/slim -d
	;;
stop)
	killall /usr/bin/slim
	;;
restart)
	$0 stop
	sleep 2
	$0 start
	;;
*)
	echo "usage: $0 [start|stop|restart]"
	;;
esac

# End of file

```

---

