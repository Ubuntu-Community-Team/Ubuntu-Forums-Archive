---
title: "Using Clonezillla To Create an Ubuntu ISO...."
date: 2013-05-23
forum: Development CD/DVD Image Testing
---

### Post by rayj00 on 2013-05-23
So, here's what I want to do:

A fresh install of Ubuntu 12.04.
Apply current updates.
Install current version of OpenStack and associated software pkgs.
Update if necessary.
Create 1 or two VM's....

I then want to use Clonezilla to create an iso DVD.

Can I subsequently use the created iso on any machine..meaning a machine with a
different CPU for instance?  If I create the iso on an i7 CPU, could I then install it on
an i5?  From experience, I know Ubuntu can install on just about anything but in this
case, I would like to be sure it will install after I create the iso.

Of course I choose Clonezilla for it's many features and it is free but if there is
a better way, please let me know.

Thanks and I patiently wait your responses...

Ray

---

### Post by deadflowr on 2013-05-23
As far I know, which ain't much, clonezilla clone exact copies of whatever your cloning.
It doesn't clone what is not there.(installer programs, etc)
You'd probably be better served using [remastersys]("http://www.remastersys.com/").

---

### Post by VMC on 2013-05-25
remastersys is no more. You can use the last image, but the author has decided to call it quits. It will now be forked to "[System Imager]("http://systemimager.sourceforge.net/")" at OS4's site.

Regarding CZ. I'm unsure what the OP really wants, but sounds like remastersys is what he's after. Also, its not just going from i5 to i7, but also there may be different architecture envolved - sound, graphics, etc.

---

### Post by wingnut2626 on 2013-06-14
I've taken a laptop hard drive from a Intel machine, put it into an AMD laptop which had TOTALLY different architecture, and it booted up like nothing happened.  Just a little food for thought....

---

### Post by monkeybrain2012 on 2013-06-14
A show stopping problem (for me anyway) with CZ is that it cannot restore to smaller partitions. So if you clone a partition of 100G say and only 50G has data you cannot restore it to a partition of 60G even though it is more than enough to house the data. This issue doesn't arise if you only use it for backup because then you would only restore it to the original partition. But if you want to clone your system somewhere else it is a problem. For that I use Fsarchiver.

---

