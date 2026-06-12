---
title: "Just Installed Ubuntu 7.04, need a bit of help."
date: 2007-05-02
forum: Desktop Environments
---

### Post by foosa on 2007-05-02
Ok, as the title says I just finished installing ubuntu 7.04 and when I boot to it, I get an error saying;

a log is being saved in /var/log/fsck/checkfa  if is writable please repair the file system manually.

How can I correct this?  Keep in mind while I have read a lot about ubuntu I am still a complete nooblet at it.

Second question,

I cannot connect to my wireless network.  I have great signal but can't connect.


Thanks.

---

### Post by foosa on 2007-05-02
Also, how can I get my display to 1680 x 1050?  The closest to that I could get was 1280 x 1050.(something close to that)

---

### Post by amaroKer on 2007-05-03
see my signature link on permissions

To see if you have write permissions:
```
sudo ls -l /var/log/fsck/checkfa
```
and look for the r in the 2nd position

Example:
```
-rwxr--r-- user group /var/log/fsck/checkfa
```
means that you, the group and all others have read permission, you alone have write and execute permission.

Again, see my signature link on permissions.  You'll want to understand this.  It's not as scary as it looks.

---

### Post by hartz on 2007-05-03
Hello Foosa,

> **foosa said:**
> Ok, as the title says I just finished installing ubuntu 7.04 and when I boot to it, I get an error saying;

a log is being saved in /var/log/fsck/checkfa  if is writable please repair the file system manually.

How can I correct this?

What is happening here is the system is hung because it is protecting itself against file system corruption.  It is trying to do an automatic "File system check" (fsck), but the problem is more complex than what can be handled automatically, so it is asking you, the human master, to intervene.

Now at this point in the startup sequence it is checking some disks before mounting them.  In order to save a log file, it needs to write to the disk, in order to write to a disk, it needs to mount it, and in order to mount it, it needs to first check that it is clean of corruption.  But the fsck is failing for at least one of your disks, and it wants to record the details of the failure in a log.

Because it is potentially doing several disks and some may have passed the check and been mounted it may or may not be able to write a log at this point in time.  That is what it means with there will be a log _IF_ the disk is writeable.

Look at the time stamp on that file using the ls command given by amaroKer - it will tell you if the file has been recently modified.

I must run now, I'll post more in a few hours.

---

### Post by hartz on 2007-05-03
Right, now what you need to do is have a look at that log file.  Has it been modified recently, and what did the system write to it, if anything.

But before you can even get to that, depending on how your system has been set up, you may need to log in first.

So the first question is, Is it asking you to log in.  If so, it will only allow you to log in as "root" and most likely, this being Ubuntu, you will not be able to log in as root.  In that case you will need to boot from a recovery disk to sort this out.  Lets hope that is not the case.

If you are already being presented with a prompt, (already logged in without providing a password) then you can start to enter commands to help the system get the disk sorted out.

Firstly, look at what file systems have been mounted and what options they have set.  This command will tell you if file systems are mounted as read-only or read-write (ro or rw ):

```
mount
```

Then check the log fsck log file.  First check its time-stamp with this command

```
ls -l /path/to/logfile
```

And to display its content, use the command

```
less /path/to/logfile
```

Please post what you find running these commands so that I and other people on here can give you more advice.  Before you start running commands, there is one more thing.  Often Linux will tell you to run a specific command to fix the file system corruption, eg fsck /dev/hda1

If any, Note that command before it scrolls of the screen.

Cheers.

---

### Post by foosa on 2007-05-03
The screen displays all the info I said above.  Then says something to the effect of log in a shell or press control D to continue to log in.  It allows me to log in as a user, but I haven't tried Root yet.

I will try to above mentioned lines and see what happens in a few hours, I have to go take a Java programming final.(I love the smell of college in the morning...)

Will get back in a few hours.


And Thanks for the replays guys.

**edit**

should I put those lines of code in the command line where I get the error?  Or in the terminal when I log in?

**/edit**

---

### Post by foosa on 2007-05-03
```
sudo ls -l /var/log/fsck/checkfs
```

Asked for my password then gave me 
```
-rw-r----- l root admin 225 2007-05-03 12:44 /var/log/fsck/checkfs
```


```
ls -l /path/to/logfile
```
Gave me command not found

```
less /path/to/logfile
```
gave me no such file.

---

### Post by foosa on 2007-05-03
I just ran 
```
less /var/log/fsck/checkfs
```

And it gave  me this,

```
log of fsck -C-R-A-a
Thu May 3 12:59:52 2007.

fsck 1.4 -WIP (14-Vov-2006)
fsck.ext3: unable to resolve 'UUID= Laba776c-ef38-497e-b36e-3845e41w0ac4'
fsck died with exit status 8

Thu May 3 12:59:52 2007
--------------------------
/var/log/fsck/checkfs (end)
```

If that helps anybody.

---

### Post by rsambuca on 2007-05-03
Looks like your fstab has the incorrect uuid number for one of your drives.  Open a terminal, and enter```
ls /dev/disk/by-uuid/ -alh
```This will give you the correct uuid numbers for your drives.

Then enter```
gksudo gedit /etc/fstab
```to open your fstab file, and change the incorrect uuid to the correct version as listed by the prior command.

---

### Post by foosa on 2007-05-03
```
ls /dev/disk/by-uuid/ -alh
```
This give this
```
jonathan@Ramit:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 120 2007-05-03 09:25 .
drwxr-xr-x 6 root root 120 2007-05-03 13:35 ..
lrwxrwxrwx 1 root root  10 2007-05-03 09:25 065ad3be-1dd4-4d41-bc84-b1a51858d6ba -> ../../sda6
lrwxrwxrwx 1 root root  10 2007-05-03 09:25 4639-0B8F -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-05-03 09:25 6163e874-ed33-41bf-89a4-87bfccae25e3 -> ../../sda7
lrwxrwxrwx 1 root root  10 2007-05-03 09:25 94CC1187CC116530 -> ../../sda1
```

```
gksudo gedit /etc/fstab
```
This shows this in a window after entering my password.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=065ad3be-1dd4-4d41-bc84-b1a51858d6ba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=94CC1187CC116530 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1aba776c-ef38-497e-b36e-3845e41e0ac4 /media/sda5     ext3    defaults        0       2
# /dev/sda7
UUID=6163e874-ed33-41bf-89a4-87bfccae25e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Not sure what to do now.

---

### Post by foosa on 2007-05-03
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=065ad3be-1dd4-4d41-bc84-b1a51858d6ba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=94CC1187CC116530 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1aba776c-ef38-497e-b36e-3845e41e0ac4 /media/sda5     ext3    defaults        0       2
# /dev/sda7
UUID=6163e874-ed33-41bf-89a4-87bfccae25e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I changed the 2 in defaults to a 0 and now all is well.  Thanks to boomslang of pbnation.com.  

Now i just need to get my wireless internet working right.  Any ideas?  I have a asus p5 w dh deluxe motherboard and use the on board wireless adapter.  I get a message saying that my hardware doesn't support the security.  Something along those lines.

---

### Post by rsambuca on 2007-05-03
I really don't think that was a very good way to fix your problem (in fact, you didn't really fix it, you just basically hid it!).  If you look at the uuid command, the sda5 drive has a uuid of 4639-0B8F, whereas your fstab has something different.

If you want to fix it, I would change the settings back to the way they were before.  Then, I would edit the line in your fstab to fix the sda5 mismatch.  After opening a terminal, ```
gksudo gedit /etc/fstab
```

Then change the line that says:```
# /dev/sda5
UUID=1aba776c-ef38-497e-b36e-3845e41e0ac4 /media/sda5...
```to ```
# /dev/sda5
UUID=[COLOR="Red"]4639-0B8F[/COLOR] /media/sda5
```

---

### Post by foosa on 2007-05-03
will do that then. 

any idea on my wireless problem?

---

### Post by rsambuca on 2007-05-03
Yeah, by changing that last number to a zero, you tell the OS to never perform a fsck on the drive - something you definitely want to have happen.

Sorry I can't help you on the wireless front. 

I'm hardwired here.:)

---

### Post by foosa on 2007-05-03
Ok, I changed what you said and now I get the error again.  Any more ideas on how to fix it?

---

### Post by rsambuca on 2007-05-03
OK, re-run those two commands and post here, I will take a closer look.

---

### Post by foosa on 2007-05-03
```
jonathan@Ramit:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 120 2007-05-03 12:41 .
drwxr-xr-x 6 root root 120 2007-05-03 16:41 ..
lrwxrwxrwx 1 root root  10 2007-05-03 12:41 065ad3be-1dd4-4d41-bc84-b1a51858d6ba -> ../../sda6
lrwxrwxrwx 1 root root  10 2007-05-03 12:41 4639-0B8F -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-05-03 12:41 6163e874-ed33-41bf-89a4-87bfccae25e3 -> ../../sda7
lrwxrwxrwx 1 root root  10 2007-05-03 12:41 94CC1187CC116530 -> ../../sda1

```



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=065ad3be-1dd4-4d41-bc84-b1a51858d6ba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=94CC1187CC116530 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4639-0B8F /media/sda5     ext3    defaults        0       2
# /dev/sda7
UUID=6163e874-ed33-41bf-89a4-87bfccae25e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

There you go.

---

### Post by rsambuca on 2007-05-03
hmmm... I am at a loss.  From the looks of things, the uuids match now.  Sorry I can't help you further.

---

### Post by foosa on 2007-05-03
Thanks for trying to help me.  Anybody else have any ideas?   

Do you think if I reformat my ubuntu partitions and re-install that it could help?  If so ill do that then.

---

### Post by foosa on 2007-05-04
do you think total uninstall and reinstall is a viable option? Or would I just end up with the same problem?

---

### Post by CameO73 on 2007-05-04
Strange problem. But you could try mounting the disk/partition by using **/dev/sda5** instead of using the UUID. This means changing the lines
```
# /dev/sda5
[COLOR=Black]UUID=4639-0B8F[/COLOR] /media/sda5        ext3    defaults        0       2
```to
```
# /dev/sda5 (UUID=4639-0B8F?)
[COLOR=Black]/dev/sda5[/COLOR] /media/sda5           ext3    defaults        0       2
```This has one disadvantage ... if you decide to add a new harddrive, the /dev/sda5 designation could change. Just keep that in mind if you ever decide to upgrade!

For your wireless problem we need more information. Could you post more details about your WLAN card (goto System -> Preferences -> Hardware Information, look under the PCI Bridge section for something with WLAN interface under it) and the type of security you want to use (WEP, WPA, WPA2)?

---

### Post by foosa on 2007-05-04
I just reformatted ubuntu and reinstalled it, and now It seems to run smoother with no booting errors.  So I think Im good to go with problem number 1.

For the WLAN,

RTL8187_wireless>usb interface
WLAN interface
>
vendor:unknown
 device:unknown
 status:status
 Bus type: usb interface
 Device typ: "net","net.80211"
 Capabilities:net
 net.80211

usb raw 
 device; unknown
 access: unknown
 status: status
 Bus type: usb 
 device type "usbraw"
 capabilities usbraw

Thats what I get. And Im using WPA.

---

### Post by CameO73 on 2007-05-04
Hmmm... here are a couple of interesting threads on this subject:

First of all [this thread]("http://ubuntuforums.org/showthread.php?p=2569360") that talks about using ndiswrapper and an alternate Windows 98 driver.

There's also a pretty clear [How-to]("http://ubuntuforums.org/showthread.php?t=329299") for Ubuntu Edgy. It doesn't seem to work for Feisty, though ... read the above thread for more info about that.

People are working on a [better Realtek driver]("http://rtl-wifi.sourceforge.net/wiki/Main_Page"). No releases yet (although you could try compiling your own if you're adventurous -- and know what you're doing!), but it will eventually be a better option than the ndiswrapper solution. But at the moment the wrapper is your best bet.

Just stumbled upon [this active thread](http://ubuntuforums.org/showthread.php?t=258732). I suggest you start with the stuff mentioned in my first link (because it's tailored for Feisty) ... if all else fails, the other threads may come in handy.

Good luck!

---

