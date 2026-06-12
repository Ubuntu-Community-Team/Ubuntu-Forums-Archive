---
title: "What does Ubuntu have for hyperterm/minicom?"
date: 2007-02-09
forum: Desktop Environments
---

### Post by levinep on 2007-02-09
I used to use minicom on Suse Linux on my Dell Latitude laptop
to access servers with no video display. What does Ubuntu have
that is comparable to hyperterm or minicom and how do I get it?
I searched the forums for both of those terms and came up with
nothing.

---

### Post by banditti on 2007-02-09
I personally like gtkterm

---

### Post by odin1965 on 2007-02-27
You can install minicom thru synaptic.

---

### Post by RonKZ on 2007-03-22
I'm having the same problems with my serial-port modem, have wasted a week already, unbelievable.  neither gnome-ppp nor kppp work for this.

running Ubuntu 6.10 x64, synaptic doesn't have minicom and doesn't find it available either.  Not certain, but believe minicom was available a week ago  ???

Also having a really difficult time trying to install setserial -- dumb instructions, tough procedure, permissions, commandline.  

No alternatives to dialup except satellite.  Will these same problems with linux occur with satellite ??

---

### Post by yabbadabbadont on 2007-03-22
> **RonKZ said:**
> I'm having the same problems with my serial-port modem, have wasted a week already, unbelievable.  neither gnome-ppp nor kppp work for this.

running Ubuntu 6.10 x64, synaptic doesn't have minicom and doesn't find it available either.  Not certain, but believe minicom was available a week ago  ???

Also having a really difficult time trying to install setserial -- dumb instructions, tough procedure, permissions, commandline.  

No alternatives to dialup except satellite.  Will these same problems with linux occur with satellite ??

```
/home/bubba $ aptitude show minicom 
Package: minicom
State: not installed
Version: 2.1-10
Priority: optional
Section: comm
Maintainer: Martin A. Godisch <godisch@debian.org>
Uncompressed Size: 913k
Depends: libc6 (>= 2.3.4-1), libncurses5 (>= 5.4-5)
Recommends: lrzsz
Description: friendly menu driven serial communication program
 Minicom is a clone of the MS-DOS "Telix" communication program. It emulates ANSI and VT102 terminals, has a dialing
 directory and auto zmodem download. backports for the stable Debian release are provided at Minicom's upstream homepage,
 which can be found at http://alioth.debian.org/projects/minicom/.

```
I just updated a couple of hours ago.  Make sure that you have all the repositories enabled.

---

### Post by RonKZ on 2007-03-22
after posting I somehow managed to use terminal command to reinstall minicom, don't remember the exact command, ?  sudo get-app minicom ?   it worked so nicely that I then did ditto for setserial.  All that downloading tar.gz stuff and fumbling with what to do with it was bypassed, thank goodness.  get-app took care of the whole thing.  

strange tho that it didn't show up anywhere in add/remove synaptic.  well anyway, I got lucky for once with linux, now will see if I can get my serial modem found and running.  I appreciate your quick reply.

---

