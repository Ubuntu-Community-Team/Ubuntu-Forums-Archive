---
title: "startup script - where do I put it?"
date: 2005-11-05
forum: Desktop Environments
---

### Post by linuxted on 2005-11-05
I'm trying to put a command to keep a backup drive unpowered.  In Fedora Core I would place this code in /etc/profile.d/, however it does not exist in Ubuntu.  I tried putting the code in .bashrc but that didn't work either.  Can someone tell me where to place this code?

Thanks

---

### Post by NewWithoutClue on 2005-11-05
"/etc/rc2.d/"
that directory is filled will symbolic links to "/etc/init.d/"
These are started at boot.
Hope this helped.

w00t,
Paul.

---

### Post by NewWithoutClue on 2005-11-06
note: "rc2.d" the number 2 would represent your default multi user runlevel.
Default is 2.

Paul.

---

### Post by Zwack on 2005-11-06
The better answer is to put it in /etc/init.d and create a symbolic link to it in /etc/rc2.d

Alternatively, some distributions (although not Ubuntu) have a rc.local file that makes for an obvious place to add small one or two line startup commands...

I hope that this helps,

Z.

---

### Post by linuxted on 2005-11-06
[QUOTE=Zwack]The better answer is to put it in /etc/init.d and create a symbolic link to it in /etc/rc2.d

Alternatively, some distributions (although not Ubuntu) have a rc.local file that makes for an obvious place to add small one or two line startup commands...

I hope that this helps,

Z.[/QUOTE]

Thanks for the help.  I'm trying it now.   Can you tell me why when I go to "User CP" it doesn't show that people have replied to my thread?  I couldn't even find this thread by searching for my username!

---

### Post by linuxted on 2005-11-06
[QUOTE=Zwack]The better answer is to put it in /etc/init.d and create a symbolic link to it in /etc/rc2.d

Alternatively, some distributions (although not Ubuntu) have a rc.local file that makes for an obvious place to add small one or two line startup commands...

I hope that this helps,

Z.[/QUOTE]

Well I put the following script in the area but it isn't working I think because I need to be root to run it:
********************************************
# This is to keep noise/power/heat low by powering off the backup
# drive

umount /dev/hdb
/sbin/hdparm -y /dev/hdb

****************************************
When I open a terminal I get:
/dev/hdb: Permission denied

Any ideas?
Thanks,

---

### Post by Zwack on 2005-11-11
Sorry I can't explain why you can't find your own post.  

As far as the script goes...

At boot it will be run automatically as root.  If you want to run it manually you can use sudo to run it as root.

sudo /etc/init.d/<script name>

it will prompt you for your password, enter that and your script will run.

I hope that this helps

Z.

---

### Post by benjamin on 2005-11-11
[QUOTE=Zwack]The better answer is to put it in /etc/init.d and create a symbolic link to it in /etc/rc2.d

Alternatively, some distributions (although not Ubuntu) have a rc.local file that makes for an obvious place to add small one or two line startup commands...

I hope that this helps,

Z.[/QUOTE]
You can also use BUM to activate/deactivate script with a GUI tools.

Bye

---

