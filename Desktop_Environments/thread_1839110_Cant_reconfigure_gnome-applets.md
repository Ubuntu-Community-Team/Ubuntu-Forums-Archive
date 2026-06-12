---
title: "Cant reconfigure gnome-applets"
date: 2011-09-05
forum: Desktop Environments
---

### Post by 5t6y on 2011-09-05
Hi, I just installed Ubuntu 10.10 on a laptop. I'm trying to get cpu scaling working. All the guides say to reconfigure gnome-applets by running 'sudo dpkg-reconfigure gnome-applets' so that the cpu frequency scaling applet can control the cpu.

Problem is, when I run the reconfigure, I get absolutely no output from the command, it doesn't let me reconfigure anything and just exits out. I saw that there was a -f option to 'force' a reconfigure, and running that I get:

sudo dpkg-reconfigure -f gnome-applets
debconf: unable to initialize frontend: Gnome-applets
debconf: (Bareword "Debconf::FrontEnd::Gnome" not allowed while "strict subs" in use at (eval 24) line 3.)
debconf: falling back to frontend: Noninteractive
/usr/sbin/dpkg-reconfigure: please specify a package to reconfigure

Any thoughts on how to fix this?

Another thing I'm trying is to user cpufreq-set. I can change the governor to userspace and that seems to work, and then I tell it to set the frequency, and it gives no errors, but has no effect on the frequency.

Thanks for any help!

[EDIT] Also, I don't know if this is any help, but this is every mention of gnome-applets in /var/log/dpkg.log

```

cat /var/log/dpkg.log | grep gnome-applets
2010-10-07 16:00:48 install gnome-applets-data <none> 2.30.0-3ubuntu3
2010-10-07 16:00:48 status half-installed gnome-applets-data 2.30.0-3ubuntu3
2010-10-07 16:00:49 status unpacked gnome-applets-data 2.30.0-3ubuntu3
2010-10-07 16:00:49 status unpacked gnome-applets-data 2.30.0-3ubuntu3
2010-10-07 16:01:36 install gnome-applets <none> 2.30.0-3ubuntu3
2010-10-07 16:01:36 status half-installed gnome-applets 2.30.0-3ubuntu3
2010-10-07 16:01:36 status unpacked gnome-applets 2.30.0-3ubuntu3
2010-10-07 16:01:36 status unpacked gnome-applets 2.30.0-3ubuntu3
2010-10-07 16:10:46 configure gnome-applets-data 2.30.0-3ubuntu3 2.30.0-3ubuntu3
2010-10-07 16:10:46 status unpacked gnome-applets-data 2.30.0-3ubuntu3
2010-10-07 16:10:46 status unpacked gnome-applets-data 2.30.0-3ubuntu3
2010-10-07 16:10:46 status half-configured gnome-applets-data 2.30.0-3ubuntu3
2010-10-07 16:10:46 status installed gnome-applets-data 2.30.0-3ubuntu3
2010-10-07 16:15:51 configure gnome-applets 2.30.0-3ubuntu3 2.30.0-3ubuntu3
2010-10-07 16:15:51 status unpacked gnome-applets 2.30.0-3ubuntu3
2010-10-07 16:15:51 status half-configured gnome-applets 2.30.0-3ubuntu3
2010-10-07 16:15:51 status installed gnome-applets 2.30.0-3ubuntu3

```

---

### Post by Frogs Hair on 2011-09-05
Here are a couple of links regarding CPU scaling . You may want to do some more searching because this seems to affect a lot of people .
 
[http://askubuntu.com/questions/26063/how-to-control-cpu-frequency](http://askubuntu.com/questions/26063/how-to-control-cpu-frequency)

[https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/637845](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/637845)

---

### Post by 5t6y on 2011-09-05
I've had cpu scaling working fine before. The problem is that in this install dpkg-reconfigure is broke. You're supposed to be able to recongure gnome-applets to allow a regular user to control the cpu speed from the applet, but the reconfigure just bails out without doing anything or without giving any error.

---

### Post by gmargo on 2011-09-05
It sounds like a corrupted file in the debconf package.

Try checking the package checksums:
```

cd /
md5sum -c /var/lib/dpkg/info/debconf.md5sums

```

---

