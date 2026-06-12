---
title: "Running a program as a process"
date: 2009-01-08
forum: General Help
---

### Post by Rahu on 2009-01-08
I'm trying to get the no-ip.com client running as a service on my ubuntu box.

They provided this init script and I thought I set it up right but it down't seem to be working

```
	#######################################################
	#! /bin/sh
	# . /etc/rc.d/init.d/functions	# uncomment/modify for your killproc
	case "$1" in
	    start)
		echo "Starting noip2."
		/usr/local/bin/noip2
	    ;;
	    stop)
		echo -n "Shutting down noip2."
		killproc -TERM /usr/local/bin/noip2
	    ;;
	    *)
		echo "Usage: $0 {start|stop}"
		exit 1
	esac
	exit 0
	#######################################################
```

I added that to a /etc/init.d/noip2 and symlinked it from /etc/rc3.d/noip2

Is there something I'm missing to make this automatically start up with the system?

---

### Post by dcstar on 2009-01-08
> **Rahu said:**
> I'm trying to get the no-ip.com client running as a service on my ubuntu box.
.......
I added that to a /etc/init.d/noip2 and symlinked it from /etc/rc3.d/noip2

Is there something I'm missing to make this automatically start up with the system?

/etc/rc**2**.d/noip2

---

### Post by Rahu on 2009-01-08
Now symlinked as /etc/rc2.d/noip2 -> /etc/init.d/noip2

Runing "/etc/init.d/noip2 start" seems to start it up fine, but it still isn't running at boot.

EDIT: I noticed all the other entries here start named with S##, does naming it like that have any impact on how it runs?

---

### Post by MighMoS on 2009-01-08
On boot, all the serives that begin with S are started in order (all the ones beginning with K are killed). BTW, you can just [code]sudo apt-get install noip2[code]As I beleive that's the client you're looking for.

---

### Post by Rahu on 2009-01-08
Awesome, thanks. Didn't expect a somewhat obscure program like that to be in the repositories :)

---

