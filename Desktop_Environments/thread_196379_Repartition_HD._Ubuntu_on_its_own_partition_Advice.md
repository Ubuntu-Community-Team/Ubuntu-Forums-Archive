---
title: "Repartition HD. Ubuntu on its own partition// Advice?"
date: 2006-06-14
forum: Desktop Environments
---

### Post by nismoskys on 2006-06-14
Hey, i was just looking for some advice on what you guys think i should do.

i have one (master)200gig HDD, and one (slave)40gig HDD.

My current setup is all of my data (OS+personal files) on a single partition on the 200gig HD that takes up 100GB, while the 40gig HD is completely unused and has nothing important on it.

I was wondering if i should repartition my master drive so that the os is on its own partition and files on their own.

i was thinking that i could just reinstall ubuntu on the master onto a 10 gig partition, so all my current data would be on the other partition, and i could just delete everything from the first partion aside from my personal files.

instead, i was thinking i could just install ubuntu itself onto the slave while keeping all of my files on the master, although im somewhat hesitant to use the 40 gig drive, i dont know why.. i guess its because i dont like the idea of os on one drive and files on another because i tried that in windows and it sucked because i had to link each folder of my files to the folder on the other harddrive. (ex. open my documents, then have a shortcut linking to the real my documents on the other hdd).
But since im running linux now, i believe its easier to mount an additional drive at a more convenient location, since i can pick where it goes, instead of being forced to have it as something like "G:/"

i dont know im not too sure right now.. im actually just waiting to get my dapper install cds in the mail to (hopefully) ensure that i get a good install.

well, if you guys have anything helpful for me, i'd appreciate it.

thanks. :)

---

### Post by morequarky on 2006-06-14
How much REAL DATA do you have?

To do anything like you speak of requires you to back up what you have. Reinstall/repartition. then output the backed-up files to the new filesystem.

You don't have any windows to mess with and that makes everything a whole lot easier.

Partitioning the filesystem on different hard drives is very possible as far as I know.  When you install, you partition your harddrive differently and make a /home partition.  I suggest you do some research on the Linux filesystem.  I am quite new at this and even I get confused as to where stuff is put and where stuff is installed.

It sounds like you have....

hda0 100GB linux
hda1 100GB free space

hdb0 40GB free space.

Is that correct?

---

### Post by nismoskys on 2006-06-14
yeah thats about right.

thanks

---

### Post by morequarky on 2006-06-14
I found this article online.  I did not write it.  Who ever did write it did a fantastic job.

The first thing that most new users shifting from Windows will find
confusing is navigating the Linux file system. The Linux file system 
does things a lot more differently than the Windows file system
This article explains the differences and takes you through the 
layout of the Linux file system 
For starters, there is only a single hierarchal directory structure.
Everything starts from the root directory, represented by '/', and then
expands into sub-directories. Where DOS/Windows had various partitions and
then directories under those partitions, Linux places all the partitions
under the root directory by 'mounting' them under specific directories.
Closest to root under Windows would be c:.
Under Windows, the various partitions are detected at boot and assigned a
drive letter. Under Linux, unless you mount a partition or a device, the
system does not know of the existence of that partition or device. This
might not seem to be the easiest way to provide access to your partitions
or devices but it offers great flexibility.
This kind of layout, known as the unified file system, does offer several
advantages over the approach that Windows uses. Let's take the example of
the /usr directory. This directory off the root directory contains most of
the system executables. With the Linux file system, you can choose to mount
it off another partition or even off another machine over the network. The
underlying system will not know the difference because /usr appears to be
a local directory that is part of the local directory structure! How many
times have you wished to move around executables and data under Windows,
only to run into registry and system errors? Try moving c:windows system
to another partition or drive.
Another point likely to confuse newbies is the use of the front slash '/'
instead of the backslash '' as in DOS/Windows. So c:windowssystem would
be /c/windows/system. Well, Linux is not going against convention here.
Unix has been around a lot longer than Windows and was the standard a lot
before Windows was. Rather, DOS took the different path, using '/' for
command-line options and '' as the directory separator.
To liven up matters even more, Linux also chooses to be case sensitive.
What this means that the case, whether in capitals or not, of the
characters becomes very important. So this is not the same as THIS or ThIs
for that matter. This one feature probably causes the most problems for
newbies.
We now move on to the layout or the directory structure of the Linux
file system Given below is the result of a 'ls -p' in the root directory.
bin/ dev/ home/ lost+found/ proc/ sbin/ usr/
boot/ etc/ lib/ mnt/ root/ tmp/ var/
/sbin - This directory contains all the binaries that are essential to the
working of the system. These include system administration as well as
maintenance and hardware configuration programs. Find lilo, fdisk, init,
ifconfig etc here. These are the essential programs that are required by
all the users. Another directory that contains system binaries is /usr/sbin. 
This directory contains other binaries of use to the system administrator. 
This is where you will find the network daemons for your system along with 
other binaries that only the system administrator has access to, but which are
not required for system maintenance, repair etc.
/bin - In contrast to /sbin, the bin directory contains several useful
commands that are used by both the system administrator as well as
non-privileged users. This directory usually contains the shells like
bash, csh etc. as well as much used commands like cp, mv, rm, cat, ls. 
There also is /usr/bin, which contains other user binaries. These binaries 
on the other hand are not essential for the user. The binaries in /bin 
however, a user cannot do without.
/boot - This directory contains the system.map file as well as the Linux
kernel. Lilo places the boot sector backups in this directory.
/dev - This is a very interesting directory that highlights one important
characteristic of the Linux file system - everything is a file or a
directory. Look through this directory and you should see hda1, hda2 etc,
which represent the various partitions on the first master drive of the
system. /dev/cdrom and /dev/fd0 represent your CDROM drive and your floppy
drive. This may seem strange but it will make sense if you compare the
characteristics of files to that of your hardware. Both can be read from
and written to. Take /dev/dsp, for instance. This file represents your
speaker device. So any data written to this file will be re-directed to
your speaker. Try 'cat /etc/lilo.conf > /dev/dsp' and you should hear some
sound on the speaker. That's the sound of your lilo.conf file! Similarly,
sending data to and reading from /dev/ttyS0 ( COM 1 ) will allow you to
communicate with a device attached there - your modem.
/etc - This directory contains all the configuration files for your system.
Your lilo.conf file lies in this directory as does hosts, resolv.conf and
fstab. Under this directory will be X11 sub-directory which contains the
configuration files for X. More importantly, the /etc/rc.d directory
contains the system startup scripts. This is a good directory to backup
often. It will definitely save you a lot of re-configuration later if you
re-install or lose your current installation.
/home - Linux is a multi-user environment so each user is also assigned a
specific directory which is accessible only to them and the system
administrator. These are the user home directories, which can be found
under /home/username. This directory also contains the user specific
settings for programs like IRC, X etc.
/lib - This contains all the shared libraries that are required by system
programs. Windows equivalent to a shared library would be a DLL file.
/lost+found - Linux should always go through a proper shutdown. Sometimes
your system might crash or a power failure might take the machine down.
Either way, at the next boot, a lengthy file system check using fsck will
be done. Fsck will go through the system and try to recover any corrupt
files that it finds. The result of this recovery operation will be placed
in this directory. The files recovered are not likely to be complete or
make much sense but there always is a chance that something worthwhile is
recovered.
/mnt - This is a generic mount point under which you mount your file systems
or devices. Mounting is the process by which you make a file system
available to the system. After mounting your files will be accessible
under the mount-point. This directory usually contains mount points or
sub-directories where you mount your floppy and your CD. You can also
create additional mount-points here if you want. There is no limitation to
creating a mount-point anywhere on your system but convention says that
you do not litter your file system with mount-points.
/opt - This directory contains all the software and add-on packages that
are not part of the default installation. Generally you will find KDE and
StarOffice here. Again, this directory is not used very often as it's
mostly a standard in Unix installations.
/proc - This is a special directory on your system. We have a more detailed
article on this one here.
/root - We talked about user home directories earlier and well this one is
the home directory of the user root. This is not to be confused with the
system root, which is directory at the highest level in the file system
/tmp - This directory contains mostly files that are required temporarily.
Many programs use this to create lock files and for temporary storage of
data. On some systems, this directory is cleared out at boot or at
shutdown.
/usr - This is one of the most important directories in the system as it
contains all the user binaries. X and its supporting libraries can be
found here. User programs like telnet, ftp etc are also placed here.
/usr/doc contains useful system documentation. /usr/src/linux contains the
source code for the Linux kernel.
/var - This directory contains spooling data like mail and also the output
from the printer daemon. The system logs are also kept here in
/var/log/messages. You will also find the database for BIND in /var/named
and for NIS in /var/yp.
This was a short and basic look at the Linux file system You do need to
have at least this basic knowledge of the layout of the file system to
fully utilize its potential. One good place to read about the file system
is this detailed document at [www.pathname.com/fhs/1.2/fsstnd-toc.html](www.pathname.com/fhs/1.2/fsstnd-toc.html) that
specifies the standard structure of the Linux file system

---

### Post by nismoskys on 2006-06-15
nice article thanks alot.. so just one more question.

using my current setup as described above..

if i were to install another copy of ubuntu onto my slave (while i have one on my master)... could i just delete everything else off the master (after ubuntu is installed on the slave) except for my /home directory, then just mount the master as /home when im running ubuntu on the slave? (im sorry this seems pretty confusing).

Also, if i were to mount the master as /home on the slave, would i have to move all the contents of the master's /home to the root of the drive so it would be read directly? 

Hope this makes sense.

thanks.

---

### Post by ifokkema on 2006-06-15
[QUOTE=nismoskys]if i were to install another copy of ubuntu onto my slave (while i have one on my master)... could i just delete everything else off the master (after ubuntu is installed on the slave) except for my /home directory, then just mount the master as /home when im running ubuntu on the slave? (im sorry this seems pretty confusing).

Also, if i were to mount the master as /home on the slave, would i have to move all the contents of the master's /home to the root of the drive so it would be read directly? [/QUOTE]
Hi,

If you install Ubuntu on your slave disk (usually hdb1), and tell the partitioner during the install that your master drive (usually hda1) should be mounted at /home, make sure you UNselect the /home partition to be formatted. After that, the install process will create a directory on your /dev/hdb1 called after your username. You then need to move your old files over to your new home dir, and delete the rest.

```
mv /home/home/<your user name>/* /home/<your user name>/
```
should do the trick.

Also, about the article, please bear in mind that this article is written for Linux in general. Debian based systems (like Ubuntu) generally don't contain self-compiled programs, and thus use the root directories slightly differently.

Ivo

---

### Post by nismoskys on 2006-06-15
oh cool

thanks alot for ur help guys.

---

### Post by morequarky on 2006-06-16
Can you point me in the direction of an article about linux filesystems more in line with Debian?

---

### Post by soonindallas on 2006-06-16
looks like para 4.3 could suit your needs:

[http://www.debian.org/doc/manuals/user/ch-files.html](http://www.debian.org/doc/manuals/user/ch-files.html)

suggested by another user on a different thread concerning a similar question.  I think it also answers your question.

---

### Post by ifokkema on 2006-06-16
[QUOTE=soonindallas]looks like para 4.3 could suit your needs:

[http://www.debian.org/doc/manuals/user/ch-files.html](http://www.debian.org/doc/manuals/user/ch-files.html)

suggested by another user on a different thread concerning a similar question.  I think it also answers your question.[/QUOTE]

Seems like a good list, although it doesn't mention /dev or /proc like the other article does.

A few other differences:
Debian/Ubuntu don't have an /opt.
Debian/Ubuntu populate the contents of /dev automatically. Tecnically speaking, it's not actually on the drive, but in memory. Idem for /proc and /sys.
Ubuntu uses /media for dynamic mount points, not /mnt.

---

