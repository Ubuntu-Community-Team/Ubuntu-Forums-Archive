---
title: "Drive access every 5 seconds"
date: 2005-08-26
forum: Desktop Environments
---

### Post by thin_king on 2005-08-26
Hello, I've decided to try Ubuntu and installed in a partition on my Thinkpad T23. However I'm getting annoyingly loud drive access clicks every 5 seconds and can't find a way to stop it. I'm fairly certain it has to do with the mount options "noatime" and/or? "nodiratime". Tried both, no difference. This what my fstab looks like now.

proc     /proc     proc     defaults     0     0
/dev/hda8    /     resierfs     notail,noatime     0     1
/dev/hda6    none     swap     sw     0      0
/dev/hdc     /media/cdrom0     udf,iso9660     ro,user,noauto
/dev/fd0     /media(floppy0    auto    rw,user,noauto
/dev/hda5    /mnt/home     reiserfs     defaults,noatime     0     1


I could use some help from someone who knows how to set this up correctly, thanks.

---

### Post by npaladin2000 on 2005-08-27
Ok, as you mentioned in the other tread you posted, it's only doing it after logon, and it only does it in Ubuntu, not Debian.  They're loaded on the same physical T23?


2 things I can think of to check out.  One is if the Debian you're running is correctly supporting and implementing frequency scaling, because T23s had it, and I KNOW Ubuntu's supporting it.  If the Debian you're running isn't, then the fan would be on full blast all the time making it harder to hear a click noise. 

just wanted to get that one out of the way, just in case. ;)  But I'd like you to check out your Debian deskop and your Ubuntu deskop after login and tell me what different apps are running. Check out the panel apps first of all.  I'd also recommend installing [BUM (Boot Up Manager)](http://www.marzocca.net/linux/bum.html) and see what services are running on each and note the differences.  A couple of main ones are Gnome 2.8 vs. Gnome 2.10, and we're using x.org versus Debian's XFree86.

Also, are they formatted as the same type of file system?  There's also the possibility of having a physical problem on your HDD  in the outer sectors, so you should really check it just in case.

---

### Post by thin_king on 2005-08-27
I think you misread part of my post. It **is** in Debian as well, just much, much quieter. I can barely hear it. I'll answer a few of your questions before I look into the apps.

Both are on the same machine. 
No fan problems on either one, off most of the time.
Both ReiserFS
Right, Debian - Gnome 2.8 & XFree, Ubuntu - 2.10 & Xorg
No peripherals connected except USB mouse and AC power.
Not on any network or internet connection ATM.

---

### Post by heimo on 2005-08-27
Check if starting laptop-mode has any effect:
 ```
sudo laptop-mode start
``` 
(if it's not started automatically)

---

### Post by thin_king on 2005-08-27
Panel apps are the standard defaults plus battery charge monitor. I removed that to make sure it wasn't that.

I think this is may be a Gnome issue. I wasn't even aware Debian was doing this at all until yesterday probably because I'm in KDE a lot. Right now I'm in KDE and there are no 5 second clicks that I can hear.

Looking into the laptop mode...

---

### Post by thin_king on 2005-08-27
I should have mentioned this already - I'm using APM,  T23s and ACPI don't work well.

---

### Post by thin_king on 2005-08-27
Yes that did it! Starting laptop-mode stops the drive access problem *smacks forehead*  #-o

---

### Post by thin_king on 2005-08-27
Thank you heimo, that's working.  :grin:  Is there a Service Manager or admin for Ubuntu where I can add this in to start up automatically? Sorry, like I said I'm much more used to KDE in Debian. A CLI command would be fine too.  ;-)

---

### Post by twelvegates on 2005-08-27
[QUOTE=thin_king]I think this is may be a Gnome issue. I wasn't even aware Debian was doing this at all until yesterday probably because I'm in KDE a lot. Right now I'm in KDE and there are no 5 second clicks that I can hear.[/QUOTE]

I think it's a combination of Gnome and a certain distribution.
It also occurs in Fedora Core 4, but not in Mandriva and FreeBSD.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=14190](http://bugzilla.ubuntu.com/show_bug.cgi?id=14190)

---

### Post by heimo on 2005-08-27
[QUOTE=thin_king]Thank you heimo, that's working.  :grin: Is there a Service Manager or admin for Ubuntu where I can add this in to start up automatically? Sorry, like I said I'm much more used to KDE in Debian. A CLI command would be fine too. ;-)[/QUOTE]

Well.. I'm not good with this stuff, so others may correct. But I'd put something like this to /etc/init.d/laptop-mode

 ```
#! /bin/sh
#

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=laptop-mode
COMMAND=/usr/sbin/$NAME
SCRIPTNAME=/etc/init.d/$NAME


case "$1" in
  start)
		echo -n "Starting $NAME:"
		$COMMAND start >/dev/null 2>&1
		echo " done."
		;;
  stop)
		echo -n "Stopping $NAME:"
		$COMMAND stop >/dev/null 2>&1
		echo " done."
		;;
  restart|force-reload)
		echo -n "Restarting $NAME"
		$COMMAND stop
		sleep 1
		$COMMAND start
		echo "."
		;;
  *)
		# echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
		echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
		exit 1
		;;
esac

exit 0

``` 

Then make sure permissions are ok and it's run on boot:
 ```
sudo chmod 755 /etc/init.d/laptop-mode
sudo chown root:root /etc/init.d/laptop-mode
sudo update-rc.d laptop-mode defaults 90

```

---

### Post by thin_king on 2005-08-27
Couldn't access the forums for a while. :-? 

The script works great heimo. Laptop-mode started on boot-up. I also have BUM now and laptop-mode is ticked in "Activate" but with a "?" in "Running" and doesn't seem to be compatible. That's ok. The essential problem I had looks solved.  :grin:  In fact it's probably running better than my Debian Gnome. I should apt-get the Laptop Mode Tools package for Debian too. Learned a lot today, thank you.

---

### Post by thin_king on 2005-08-27
Forums are acting weird, not updating.  :? 

The script works great heimo. Laptop-mode started on boot-up. I also have BUM now and laptop-mode is ticked in "Activate" but with a "?" in "Running" and doesn't seem to be compatible. That's ok. The essential problem I had looks solved.  :grin:  In fact it's probably running better than my Debian Gnome. I should apt-get the Laptop Mode Tools package for Debian too. Learned a lot today, thank you.

---

### Post by thin_king on 2005-08-27
Doesn't look like my post got posted.   :|

---

### Post by thin_king on 2005-08-28
Looks like the forums are better now, couldn't access them for a long while yesterday. 

The script works great heimo. Laptop-mode started on boot-up. I also have BUM now and laptop-mode is ticked in "Activate" but with a "?" in "Running" and doesn't seem compatible. That's ok. The essential problem I had looks solved.  :grin:  In fact it's probably running better than my Debian Gnome. I should apt-get the Laptop Mode Tools package for Debian too. Learned some important things for my Thinkpad with Gnome, thank you.

---

