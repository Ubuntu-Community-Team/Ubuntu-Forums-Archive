---
title: "configure-trackpoint"
date: 2005-10-26
forum: Deferred/Invalid Requests
---

### Post by Jingo on 2005-10-26
Nice GUI for configuring the trackpoint of IBM/Lenovo Thinkpads.

[http://tpctl.sourceforge.net/configure-trackpoint.html](http://tpctl.sourceforge.net/configure-trackpoint.html)

---

### Post by shartrec on 2005-10-29
[QUOTE=Jingo]Nice GUI for configuring the trackpoint of IBM/Lenovo Thinkpads.

[http://tpctl.sourceforge.net/configure-trackpoint.html](http://tpctl.sourceforge.net/configure-trackpoint.html)[/QUOTE]

I downloaded the source from the above location but cannot get it to compile.  When I run ./configure I get " error: Library requirements (libgnomeui-2.0) not met ".

I can't find any package for libgnomeui-2.0 to install in the Breezy repositories.

---

### Post by emendelson on 2005-10-30
Install libgnome2-dev through apt-get or synaptic; this lets you build the program. I still can't it to work, even after running the update-rc.d command mentioned in the README and restarting. 

But this won't work in Breezy, I think, because it depends on a kernel patch which I don't think is included in Breezy.

---

### Post by shartrec on 2005-10-31
Thanks,  I also had to install libgnomeui-dev and now it compiles and installs but...

When I try to run the GUI I get "You do not have permission to configure trackpoint. Please run this program as root."    Well I would, except I already was running it as root (both sudo and su to root).

Also when I run "/etc/init.d/trackpoint start" I get a lot of   "Permission denied"
 messages and the (no mouse is configured).  I presume this is because I need the kernel patch.  

Oh well,  It was nice to live in hope a little while.

---

### Post by jdong on 2005-11-11
DEFERRED -- Extras.

---

### Post by JoNas-fr on 2006-04-29
[QUOTE=shartrec]
When I try to run the GUI I get "You do not have permission to configure trackpoint. Please run this program as root."    Well I would, except I already was running it as root (both sudo and su to root).
[/QUOTE]

I have the same problem and i'm still looking for a solution. My trackpoint works fine but I can't click on the tiny button in the middle of the keyboard to simulate a 'click'..

I'm a linux newbie so if someone can help me, i'll appreciate it! Thanks :D  


For information i'm on Ubuntu 5.10 Breezy Badger (kernel 2.6.12.10-i386).

---

### Post by mrpister on 2006-07-11
The trackpoint settings path has changed. This patch should fix the problem on a T43, but have not confirmed on other models.
[LIST]
[*]Download the attached patch file to /tmp
[*]Download [configure-trackpoint]("http://sourceforge.net/project/showfiles.php?group_id=1212&package_id=136714&release_id=420483").
[/LIST]

```
$ tar xzf configure-trackpoint-0.3.3.tar.gz
$ cd configure-trackpoint-0.3.3
$ patch -p1 < /tmp/configure-trackpoint-0.3.3.patch.txt
$ ./configure
$ make
$ sudo make install
```

---

### Post by TestUser on 2006-07-29
Hi

Thank you for your advice, I used your text file and edited the path without serio2. No errors when I run but I do not get it, how to make the values remain after reboot?

I tried to edit the press_to select_ in /sys....

Any advice?

Thank you in advance
TU

---

### Post by MountainX on 2008-03-24
same issue here - how do I make the values persist after reboot?

T61p Gutsy

---

### Post by MountainX on 2008-04-04
> **MountainX said:**
> same issue here - how do I make the values persist after reboot?


edit /etc/sysfs.conf

include lines like this:
```
#trackpoint configuration
devices/platform/i8042/serio1/serio2/speed=175
devices/platform/i8042/serio1/serio2/sensitivity=160
devices/platform/i8042/serio1/serio2/inertia=10

```

You can read this link for infomation about the path and values:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

To make it easier to edit this file, one could define an alias in /etc/bash.bashrc
```
alias settrackpoint = 'sudo nano /etc/sysfs.conf'

```

References:
[http://ubuntuforums.org/showthread.php?p=4579287](http://ubuntuforums.org/showthread.php?p=4579287) - nice GUI for trackpoint config

 [http://ubuntuforums.org/showpost.php?p=4578430&postcount=8](http://ubuntuforums.org/showpost.php?p=4578430&postcount=8) - my post with a bunch of good links

---

### Post by experttease on 2008-06-09
I have a slightly different problem. Everything is working when I change, apply and save settings, but when I restart the settings are lost, it's really annoying! the deafult speed for the trackpoint is mind-numbingly slow and...err, pointless.

Anyone know why I'm failing with this?

---

### Post by MountainX on 2008-06-09
> **experttease said:**
> I have a slightly different problem. Everything is working when I change, apply and save settings, but when I restart the settings are lost, it's really annoying! the deafult speed for the trackpoint is mind-numbingly slow and...err, pointless.

Anyone know why I'm failing with this?

Did you see my post above? [http://ubuntuforums.org/showpost.php?p=4652660&postcount=10](http://ubuntuforums.org/showpost.php?p=4652660&postcount=10)

That's how I solved it.

---

### Post by experttease on 2008-06-09
Yeah, sorry, I read half the thread and assumed the rest would be about the same thing, then I realised my error. The thread is about the GUI configure program isn't it? Anyway, I'll give your stuff a shot and get back if I have problems. Thanks dude

---

### Post by experttease on 2008-06-09
OK I tried your suggestion but the sysfs.conf file wasn't there; I created it and entered the data, set the configure-trackpoint program and restarted. It didn't work.

So I looked in etc/trackpoint.conf (the file it alters and claims to save but doesn't) and there was code like yours but which I had changed in the GUI program, but it won't save it.

Now, having followed the link back the the thinkwiki page, I've edited the rc.local file to include the settings I chose, and rebooted but they too did nothing. The rc.local file wasn't where indicated in the thinkwiki document, but in the /etc directory itself.

Any further ideas?

---

### Post by camper365 on 2009-06-07
I don't have a problem with restarting, but when I resume from standby or hibernate, it doesn't work.

---

### Post by kaushikgaurav on 2011-08-28
I use sysfsutils to configure trackpoint on my X61 tablet running Ubuntu 11.04.
The problem is everytime I reboot my computer I have to reconfigure it again to restore sensitivity.

I have already tried the above mentioned links but they don't help.

Please Help!
Gaurav

---

### Post by y0h@nn on 2011-11-26
Hi all,

Here is my workaround for this problem. Add this line to your /etc/rc.local :

echo "`grep "serio" /etc/sysfs.conf | sed 's/\(.*\)=\(.*\)/echo \2 > \/sys\/\1/'`" | sh

It just transforms the "param=value" from sysfs.conf to "echo value > /sys/param"

It works perfectly on my X220 with Ubuntu 10.04!

Cheers!

---

