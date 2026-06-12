---
title: "very basic linux question on changing permissions on a dir"
date: 2005-11-18
forum: Desktop Environments
---

### Post by tommythecat on 2005-11-18
To open I am toatlly new to *nix

I have been fumbling through this brave new world and have a very basic question:

I mounted the ntfs windows partition on my dual-boot laptop.  I was able to copy the desired files (images and mp3s) to my /home/username directory, but the new directory I created is locked out and I cannot browse it unless I su to root and ls from a terminal.

My question is: How do I change permissions on directories and files residing in those directories in linux?

I read the man for chmod which is what seemed liek the right approach to me, but being a total newb I am lost as to how to apply the desired permissions.  I basically want to give my normal user account full permissions on the new directory I copied from my ntfs partition.

Can anyone help me with this?

Any help will be greatly appreciated.

Thanks.

---

### Post by cstudent on 2005-11-18
sudo chown -R username:usergroup /directoryname

also take a look at in terminal:

man chown

info chown

---

### Post by tommythecat on 2005-11-18
Thank you very much for the speedy and concise reply.  I'll give it a shot in the morning... must sleep now very sick 

I hope the head cold virus I have doesn't spread via this interwebthingy or else I may have infected you ;)

---

### Post by cstudent on 2005-11-18
Glad to help. I'll drink some OJ.

---

### Post by tommythecat on 2005-11-19
It worked like a charm thank you

---

### Post by thojoh on 2005-11-21
Hi there, 

I've had a similar issue, found this thread and tried the suggestion, but it does not seem to work with me.

I was trying to change the owner of sda5 (which is my seperate data-partition) to my general user (thojoh), so that all my applications can read and write to that partition. (At the moment it does not work too well because 'root' is the owner).

But the system does not allow me to.

This is what I tried:

sudo chown -R thojoh:thojoh /media/sda5

The output is a long list of all the files on sda5 with everytime the note 'Operation not permitted' e.g.: 

chown: changing ownership of `/media/sda5/Werk/rooms.doc': Operation not permitted

What am I doing wrong? :confused:

---

### Post by frodon on 2005-11-21
What is the file system of your partition ?
I ask you that because FAT32 don't support ownership and unix rights, so if you have a FAT32 partition it's normal.
If you have a read only access to your partition the problem could come from your fstab configuration, so could you post your fstab file in the next post ?
```
sudo gedit /etc/fstab
```

---

### Post by thojoh on 2005-11-21
Yes, it is a FAT32 partition... :(   Is that the end of the story, then?


One of the simple problems I have is that I can't give 'Sound Juicer' a Music Folder that is located on sda5 to write music to. At the moment I have to write it first to /home and then copy it into sda5. But also that is not straigtforward and easy as I have to log in as 'root' to be able to do so. (I created a 'root' File-Browser to help me, but this all feels a bit like patch-work. No elegant long-term solution.

I chose for a FAT32 partition in the first place so that
1. I can access all relevant data also from my WindowsXP partition.
2. I can easily upgrade ubuntu in the future, even with clean-installs if necessary while my data remains untouched.


Is there anything I can do to make my life easier?


oh, and here's my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda5       /media/sda5     vfat    defaults        0       0
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by frodon on 2005-11-21
Don't worry, i also use FAT32 and enjoy using it !
Your problem is just to add some options in in your fstab file in order to allow a simple user to write on the partition.
So all you have to do is to modify your fstab file like that : ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda4 / ext3 defaults,errors=remount-ro 0 1
/dev/sda7 /home ext3 defaults 0 2
**/dev/sda1 /media/sda1 vfat iocharset=utf8,rw,user,exec,umask=000 0 0**
/dev/sda2 /media/sda2 ntfs defaults 0 0
**/dev/sda5 /media/sda5 vfat iocharset=utf8,rw,user,exec,umask=000 0 0**
/dev/sda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```Then do a **sudo mount -a **or reboot if nothing changed

---

### Post by thojoh on 2005-11-21
ahem, now my sda5 partition has vanished...

:???: 

I will not panick, as I guess it is all rewindable. But maybe you can tell me what went wrong. I did what you suggested, but tried it first only on sda5, so my fstab file looks now like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda5       /media/sda5     iocharset=utf8,rw,user,exec,umask=000 0 0
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Normally, sda5 mounts on start up and is displayed on my desktop, but now, after rebooting, there is only sda1 and sda2 left.
When I look into the /media directory with the File Browser then the Folder sda5 is still visible but when I click on it, it appears to be empty.

What might have gone wrong?

---

### Post by frodon on 2005-11-21
It's because the partitions haven't been mounted, it's strange ...
Add the auto parameter in your fstab line, this option tell explicitly to mount the partition on startup. Your fstab line would look like that : ```
/dev/sda5 /media/sda5 vfat iocharset=utf8,auto,rw,user,exec,umask=000 0 0
```

---

### Post by thojoh on 2005-11-21
Does not do the trick, unfortunately.

Same situation after including the auto-command and rebooting...

Did we make any typing errors maybe (I actually don't know what it is I am doing with the options in fstab - at the moment I am simply copy-pasting your suggestions.) 

My fstab look now like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda5       /media/sda5     iocharset=utf8,auto,rw,user,exec,umask=000 0 0
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by markd on 2005-11-21
I don't pretend to be an expert, but I notice that you have omitted the "type":

/dev/sda5 /media/sda5 **vfat** iocharset=utf8,auto,rw,user,exec,umask=000 0 0

Don't know if that's the cause of the problem, but I think the presence of options is significant in fstab.

---

### Post by frodon on 2005-11-21
**markd** is right, the **vfat** type is missing, all should be good now !

Edit : lol markd you're right, i didn't see that, thank you ;)

---

### Post by cstudent on 2005-11-21
[QUOTE=thojoh]Does not do the trick, unfortunately.

Same situation after including the auto-command and rebooting...

Did we make any typing errors maybe (I actually don't know what it is I am doing with the options in fstab - at the moment I am simply copy-pasting your suggestions.) 

My fstab look now like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda5       /media/sda5     iocharset=utf8,auto,rw,user,exec,umask=000 0 0
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/QUOTE]

Comparing to the example frodon gave, vfat is missing from /dev/sda5

Did you make a copy of fstab before you started?

sudo cp /etc/fstab /etc/fstab_backup

If you didn't I would still back it up. You could use the where you first posted it to set it back to it's original configuration.

Bill

---

### Post by thojoh on 2005-11-21
Yep, thanks markd, thanks Bill... The missing vfat was the problem.

My own stupid pasting mistake!

And thanks a lot frodon, now indeed it works perfectly fine and my user account has all the access I need.  :p 

Is it easy to explain what I exactly did with the options  
iocharset=utf8,auto,rw,user,exec,umask=000

(so that I learn a bit more about ubuntu and helping myself)

Or is that really cryptic programming stuff?

---

### Post by thojoh on 2005-11-21
And can I do the same to my ntfs partition? (I think I know already that I can't write to ntfs from linux, but as root user I can at least read from it, while as normal user i am barred from that partition.)

So could I do this, editing sda2:

/dev/sda2 /media/sda2 ntfs iocharset=utf8,rw,user,exec,umask=000 0 0

or could that be dangerous...? :rolleyes:

---

### Post by frodon on 2005-11-21
You could use these options for your ntfs partition : ```
/dev/sda2 /media/sda2 ntfs nls=utf8,user,auto,umask=0222 0 0
```Endeed there's no write support for NTFS for the moment. There's the captive project which allow you to write on NTFS but it's not really reliable.

---

### Post by thojoh on 2005-11-21
That works perfect. I still don't know what the changes mean, but they do the trick. 

:razz: Thanks a lot, frodon!

---

### Post by frodon on 2005-11-21
**Utf8** specify the character support, **user** means to allow a simple user to handle the partition (it's the same than rw,exec options i think), and the mask specify the default rights for each files : 000 means r,w,x for all (you, your group, and everybody), 222 means r,x rights for everybody.
It's because 2 in binary is 010, and unix rights are rwx, so 2 will mask the w parameters therefore the write rights.

Is it enough clear ?

---

### Post by thojoh on 2005-11-22
Yes I get it. Thanks for the explanation.

And why do you write 'iocharset=' in hte line for the fat32 partitions and 'nls=' for the ntfs partition?

---

