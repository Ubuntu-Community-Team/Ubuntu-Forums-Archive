---
title: "Matlab and libc.so.6 problem"
date: 2005-01-22
forum: Desktop Environments
---

### Post by rdking on 2005-01-22
I am brabd new to the distro, and must say that only after a couple of hours with it, I am impressed.  It has fuctionallity, simplicty and adaptablity that I like.  Comming from mandrake and fedora, it is a nice change.  My problem is, I am trying to re-install matlab, for academic purpose.  I have the 3 cd's and was running happily on Fedora 3 until the whole box crunched, cause of some bad yum updates.  I am trying to run the following as root:

sh /media/cdrom/install -x

and recieve for output:

/media/cdrom/install: line 1: /lib/libc.so.6: Permission denied
/tmp/4366tmwinstall/install: line 1: /lib/libc.so.6: Permission denied
/media/cdrom0/install: line 1: /lib/libc.so.6: Permission denied

the only answers from people from other distro was to make sure my fstab file allows for the cd drive to be executable (exec...isn't that the one).  No ideas, but need this to work for school...and don't won't to give up on a so far well running and designed distro.

some elementary specs....just installed today....AMD 2600, kernel 2.6.8

---

### Post by rdking on 2005-01-22
just in case it is of importance here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto,exec  0       0

---

### Post by ow50 on 2005-01-22
I never had problems installing matlab, but i get the same error when starting matlab from the command line. Matlab runs fine though. Also, I cannot start matlab from the menu, it always crashes after the splash screen.

---

### Post by rdking on 2005-01-22
ow50

I do believe that if you try and use a launcher in a graphical interface make sure it is set up to run the program in a terminal.  That was the only way I could get it to run in fedora as well.  The terminal will stay open in the background and automatically shut down when matlab is exited

---

### Post by rdking on 2005-01-22
well got it working and ow50 in the laucher settings simply add this as the command:

nohup "path"/matlab

cheers

---

### Post by ow50 on 2005-01-22
[QUOTE=rdking]nohup "path"/matlab[/QUOTE]
Thanks. That did the trick.

---

### Post by daniels on 2005-01-22
The problem here, and with other devices like this, is that they are mounted 'noexec', so you cannot natively execute things from them.

---

### Post by timotten on 2005-01-30
I'm running MatLab 7.0.1, Debian Sarge, and Gnome 2.8.1. I found this thread doing a Google search. Since the thread is recent, I thought I'd quickly add that the nohup trick didn't work for me. I later found

[http://www.mathworks.com/support/solutions/data/1-1B5ZV.html?solution=1-1B5ZV](http://www.mathworks.com/support/solutions/data/1-1B5ZV.html?solution=1-1B5ZV)

which suggested running, e.g. 'setsid /usr/local/bin/matlab -desktop'. That worked for me.

---

