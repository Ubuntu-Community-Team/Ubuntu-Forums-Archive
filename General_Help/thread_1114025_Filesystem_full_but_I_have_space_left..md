---
title: "Filesystem full but I have space left."
date: 2009-04-02
forum: General Help
---

### Post by fooboo0 on 2009-04-02
I have xubuntu installed on an 8gb usb memory stick.
It boots to a folder called /cdrom and in this folder is a sub folder called /filesystem.

I have 6gb free space left on the stick but the filesystem folder says it has 54mb left.

Does anyone know how I can allocate more of the free space to the filesystem folder so I can install more software?

If so can it be done without wrecking the current install i.e. will I have to reinstall?

I keep getting messages about the filesystem being full when I try to install new packages.

---

### Post by kpatz on 2009-04-02
From a terminal type **mount** and post what you get.  Also type **df -h** and post what you get.

Typically the LiveCD/USB boots into a RAM disk where your active root filesystem resides.  You may have to increase the size of that RAM disk, or partition on the USB drive, depending on how the filesystems are set up.

---

### Post by fooboo0 on 2009-04-02
I installed this using a wizard so I'm not too up on how it all works. The machine it's running on has 512mb ram. Below is what I got from running those commands.

**_Output from mount:_**
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /cdrom type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)

**_Output from df-h:_**
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M     0  244M   0% /lib/init/rw
varrun                244M  108K  244M   1% /var/run
varlock               244M     0  244M   0% /var/lock
udev                  244M  2.8M  241M   2% /dev
tmpfs                 244M     0  244M   0% /dev/shm
rootfs                1.2G  1.1G   54M  96% /
/dev/sda1             7.9G  1.8G  6.1G  23% /cdrom
/dev/loop0            567M  567M     0 100% /rofs
tmpfs                 1.0M   16K 1008K   2% /tmp
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 244M  2.0M  242M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp

---

### Post by bcom on 2009-04-02
Here is a possibility:  There is an invisible folder .Trash that Nautilus creates on a USB stick whenever you delete anything on it.  The folder fills up with files.

Possible solution: Right-click the USB and select Unmount Volume.  You should then be given the option to Empty the Deleted Items. Click Empty and then remove the USB from the computer.  Then, reinsert the USB and remount it.

---

### Post by fooboo0 on 2009-04-02
It's not giving me the option to unmount the usb stick. The usb stick is the only storage this machine has so possibly it might not like me unmounting what it's using at the moment?

I haven't really deleted much either. The system was a fresh install fairly recently and has sat untouched for a while. I've never had more than 2gb of files on it and it's an 8gb stick. 
The partition editor (Gparted) is reporting that the whole stick is 7.87gb and that 1.79gb are used and 6.09gb is unused.

---

### Post by bcom on 2009-04-02
Here is a command that I found helpful with regard to disk utilization:

Open a terminal and cd to the USB Drive, at the command line type:
 sudo du -xhc --max-depth=1

The format of the output is a little easier to read and it will tell the size of specific folders.  It will also show you the size of the hidden .Trash folders.

---

### Post by fooboo0 on 2009-04-02
This is what I got:

8.3M    ./sbin
5.9M    ./bin
4.4M    ./etc
212M    ./var
16K     ./lost+found
1.4G    ./usr
0       ./rofs
0       ./tmp
99K     ./root
281M    ./home
4.0K    ./cdrom
101M    ./lib
1.7M    ./boot
0       ./dev
0       ./media
0       ./mnt
0       ./opt
0       ./proc
0       ./srv
0       ./sys
2.1G    .
2.1G    total

---

### Post by bcom on 2009-04-02
OK!  Its just as you thought, the USB is not full.

I did a quick check on the Internet.  It appears that it may not be uncommon for Ubuntu to misreport disk usage on USB sticks.

You might have to do a search and include the brand of your USB in the search.

Sorry, I wish I knew more.

---

### Post by fooboo0 on 2009-04-02
Thanks for your help. I'm clueless and still learning so you got me further than I was.

---

### Post by chammi on 2009-05-23
I have a similar problem:  I have a Live USB but I can't boot it because of the disk space thing. 

does anyone know how I can at least boot into a plain terminal so I can access the disk?  

Right now I am on a LiveCD but since the USB is all Wubi, I can't go in and delete/clean/etc.  I have to boot from the USB to get the filesystem mounted before I can work on it.

---

### Post by chammi on 2009-05-23
Okay.  I followed this tutorial and I can boot now!  [http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

The bad news is that I seem to have wiped out all of my persistent files.  (I suspected this might happen so the entire old USB disk was backed up to a HDD)

So problem still not solved.

---

### Post by chammi on 2009-05-23
Okay. So now I have the USB loop filesystem expanded (but formatted)  and a backup of the old one (that wouldn't boot) on a hard disk.

I am now booted into the live USB and 


I followed the advice here
[http://ubuntuforums.org/showthread.php?t=1028564](http://ubuntuforums.org/showthread.php?t=1028564)

to mount the backup.

Rock.  I can see my home folder.  So at least the data I have saved there is accessible to recover.  Now MAYBE I can just copy files over and *possibly* even copy my system settings and stuff as well (though I might have to do that from a Live CD..hmm.. but then the destination filesystem would need to be mounted as well..)

I am HOPING that I can just open nautilus with gksudo and then copy and I won't corrupt anything by copying (for example, a file with information about the size of the loop filesystem copiedto a larger fs.)

---

### Post by chammi on 2009-05-23
Okay.  That worked about half as well as I want. Some things evidently didn't copy because some, but not all of my apps are in place. 

I shutdown.

Then logged on with a Live CD


I copied the half-right casper to my HDD just in case this doesn't work.


Then mounted BOTH the half-right casper  (as finalcasper)
and the backup of my original (as donorcasper)

Using gksudo to launch nautilus,  turned on "view hidden files"  and I tried to copy the files over to merge them. No luck. I was out of disk space on the USB.  So I just deleted everything and THEN copied over from the donor.


There is a better way to do this, because I hit a few errors "unable to copy special file"  these were things like devices.  I hoped they would be rebuilt upon booting.


Then I rebooted from the USB.

I had several error messages, which were helpful enough for me to solve. Basically, (I KNEW this might happen)  my HOME directories didn't have the right permissions.

The fix was to alt-ctrl-f4 (or really any free F number) 

and then 

sudo chown -hR ubuntu ~   

This gives "ubuntu" ownership of the home folder and all sub files and folders.  The SUDO is important here.   

Also, if your root user is not ubuntu, that will change.



I have two other users on my system, so to correct them, I just repeated the command.  But put the user name and location of their home folder.

So, for  example, if I want to fix the permissions for user "diddlydoo", I would type 

sudo chown -hR diddlydoo /home/diddlydoo

After rebooting, things seem okay.  I will cross my fingers.



DISCLAIMER -- I am still rather new to ubuntu so take these instructions with a grain of salt and always make backups and keep a Live CD handy!

---

