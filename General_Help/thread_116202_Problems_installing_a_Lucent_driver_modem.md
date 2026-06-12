---
title: "Problems installing a Lucent driver modem"
date: 2006-01-12
forum: General Help
---

### Post by jnoreiko on 2006-01-12
I am following the [instructions on the wiki]("https://wiki.ubuntu.com/DialupModemHowto") for my modem. 

I've determined it's supported by the Lucent driver.
I have a completely fresh install of 5.10, and when I get to this step:

```
sudo modprobe lt_serial
```

I get a message FATAL: module not found (I'm not in front of it, so wording might not be exact)

---

### Post by batholith on 2006-01-13
I'm having the same problem.  

I've tried several methods to install drivers for my modem, but being new to linux I'm not getting anywhere...

Please help!

---

### Post by hajk on 2006-01-13
I recommend that you download a Debian driver package from

[http://linmodems.technion.ac.il/packages/ltmodem](http://linmodems.technion.ac.il/packages/ltmodem)

for the version of your kernel; use the command "uname -r" to find what that number version is.

Then install it with the command 

sudo dpkg -i <package-name>.deb 

after which the command "sudo modprobe ltserial" should load the two modules "ltserial" and "ltmodem". Check with "cat /proc/modules | less" whether this is the case. You might also check that /dev/ttyLTM0 has been made, and that /dev/modem is a symlink to it. 

If all this checks out, you're all set to configure the interface ppp0 in System/Administration/Network. Should you use Firestarter set up for another interface, then you should switch it off, because otherwise the nameservers provided by your provider won't work. 

The modules should load automatically the next time you boot. 

Have fun.

---

### Post by jnoreiko on 2006-01-14
I can't see what I'm supposed to download from that site.


Do the wiki instructions only work for some Lucent modems? Should they be updated?

---

### Post by hajk on 2006-01-14
Really now? There is a directory at that site with a name starting with 2.6....
That is the Linux kernel main version. So, click on it, then you'll see a great many packages ready for download. My own installed kernel version is 2.6.12-10-686, and lo, there is a package that carries that name. You may have installed kernel version 2.6.12-10-386, and you'll see a package that carries that name as well (dated 13 January 2006, so really up-to-date). 

Anyway, one of these packages (the one for your specific kernel, that's really important) should be downloaded, and then installed.

I would say, go at it and enjoy the experience.

---

### Post by jnoreiko on 2006-01-15
[QUOTE=hajk]I recommend that you download a Debian driver package from

[http://linmodems.technion.ac.il/packages/ltmodem](http://linmodems.technion.ac.il/packages/ltmodem)

for the version of your kernel; use the command "uname -r" to find what that number version is.

Then install it with the command 

sudo dpkg -i <package-name>.deb[/QUOTE]

That command produces errors:

```
Selecting previously deselected package ltmodem-2.6.12-9-386.
(Reading database ... 56794 files and directories currently installed.)
Unpacking ltmodem-2.6.12-9-386 (from ltmodem-2.6.12-9-386_8.31b1_i386.deb) ...
Setting up ltmodem-2.6.12-9-386 (8.31b1) ...
ln: creating symbolic link `LTinstall.txt' to `/usr/share/doc/ltmodem-2.6.12-9-386/LTinstall.txt': Operation not permitted
/var/lib/dpkg/info/ltmodem-2.6.12-9-386.postinst: line 107: gcc: command not found
cut: the delimiter must be a single character
Try `cut --help' for more information.
cut: the delimiter must be a single character
Try `cut --help' for more information.

Diagnostic information and Guidance is being written to /usr/share/doc/ltmodem-2.6.12-9-386/LTinstall.txt

```

Doing the modprobe command after produce the same fatal error as before.

---

### Post by hajk on 2006-01-15
OK, at least you're getting the hang of it. I notice that you are running behind on your installed kernel -- version 2.6.12-9-386 -- the current one for the basic 386 instruction set is 2.6.12-10-386. I suggest that you update it, or -- if you have a more recent Pentium or Celeron processor -- update to the 2.6.12-10-686 version, then try the ltmodem deb package for that kernel. That one worked for me, so if that still gives error messages then we know that it must be some other problem...

---

### Post by jnoreiko on 2006-01-15
I'm running kernel from the 5.10 installation CD.

I am not going to muck around updating my kernel. I have no idea how to do that. I just want to get my modem working with this OS that is meant to be 'for human beings'.

---

### Post by hajk on 2006-01-15
Well, I already suspected that was the real problem. You should understand that some updating and tweaking of an installed system is an integral part of the Linux experience. In some cases even necessary, as with security updates; in other cases just the smart thing to do, as with some of the backport packages.

You say you don't even know how to update the initial install, which can only mean that you haven't tried Synaptic and the rest of the Debian "apt-get" package management system. The required "hand-holding" files are even included on the Ubuntu installation CD... In addition, there is a lot of help available on the forums (if you ask nicely).

I do hope you'll reconsider, otherwise -- as much as I hate to say it -- you would be better off sticking with Windows.

---

### Post by jnoreiko on 2006-01-15
I've connected that machine through its ethernet connection to my router, and Synaptic didn't suggest updates. In fact, after a year of running Ubuntu, I've never had Synatic suggest a kernel update.

I wouldn't mind if there were a big sign saying "This modem is not supported". But the page on the wiki clearly purports to be instructions on how to get this modem to work. The instructions do not work.

---

### Post by Master Planeswalker on 2006-01-16
I am having a similar problem, only that I can't find an appropriate driver for the 2.6.10-5-amd64 architecture. Any help would be very appreciated.

---

### Post by jnoreiko on 2006-01-19
*bump*

The wiki needs to be updated.

---

### Post by jnoreiko on 2006-02-16
*second bump*

If there is no solution to this problem, could a member of the Ubuntu team update the wiki page to say that this modem type is not reliably supported?

---

### Post by beartard on 2006-02-16
i have a Sony Vaio laptop with a lucent-chip modem.  Unfortunately, mine is one that has no free drivers available for *any* distribution of Linux.  Could yours fall in this category?  If so, I think the pay drivers are like $30, but I never wanted dialup that badly.

---

