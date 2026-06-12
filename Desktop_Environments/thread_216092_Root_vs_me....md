---
title: "Root vs me..."
date: 2006-07-14
forum: Desktop Environments
---

### Post by Hotwhlz85 on 2006-07-14
Noob back with another question guys and gals...

Yesterday I installed Ubuntu but it created partitions I wasn't real happy with on this 250Gb hdd.  So tonight I re-partitioned them to look more like some of the suggestions I've seen.  My largest partition (125Gb) would never mount.  I finally opened disk manager and saw that it had no label.  I tried making the label home but it never would work.  After much head scratching I reasoned that I already had a partition called /home and couldn't have two of em.  So I named it /documents.  Then I could enable the partition.  So far so good.  Now I can mount the partition but when I try to write to it I get an error message that tells me it's owned by root and I can't make changes to it.  I know I had to use my password to get into disk manager but I used the one for my login.  Best I can remember I never set a password for root.  

I searched this forum and found a post where someone had forgotten his root password.  Someone told him to boot into recovery mode and set a new password for root.  I figured I could do the same, login as root, and give myself permission on the /documents folder....thus solving my troubles.  Assigning the password went smoothly.  Then when I go to login as root it tells me the admin can't sign in here!!!!  So where does the root login?

I appreciate all the help and patience I've found on this forum, ya'll rock!  Thanks for taking the time to help.

Ron

---

### Post by TheBlackNoodle on 2006-07-14
As far as I know, Ubuntu has no root account. Everything you need to do through root can be done with sudo. Failing that, you can try this:

Open a terminal.
Type 'sudo chown -R username /documents' where username is your username (duh).

Now you "own" these files rather than root. See if that works.

---

### Post by Hotwhlz85 on 2006-07-14
Thanks for the quick reply TBN.  I'm with you, I didn't think Ubuntu used root either but it's sure blocking me from this folder.  I pasted your code but I just get an error message:

[IMG]http://www.carolinadreamin.net/KC/Screenshot.png[/IMG]

I pretty much suck at command lines.  Can you tell where I went wrong?  

Thanks again for your help.

Ron

---

### Post by aysiu on 2006-07-14
It appears that /documents doesn't exist.

Can you try these commands? ```
cd /
ls
cd /documents
```

---

### Post by Hotwhlz85 on 2006-07-14
Hi aysiu.  Done.  Here's what it gave me:

[IMG]http://www.carolinadreamin.net/KC/Screenshot-1.png[/IMG]

Ron

---

### Post by aysiu on 2006-07-14
In the list of folders and files within the top-level directory, I don't see any folder called *documents*.

---

### Post by Hotwhlz85 on 2006-07-14
Neither do I.  Here's where I DO see it though:

[IMG]http://www.carolinadreamin.net/KC/Screenshot-2.png[/IMG]

I think I know less and less about this stuff by the minute.  ](*,)

---

### Post by Hotwhlz85 on 2006-07-14
And here is where it tells me that I can't change the folder:

[IMG]http://www.carolinadreamin.net/KC/Screenshot-3.png[/IMG]

Ron

---

### Post by aysiu on 2006-07-14
Ah, much better.

It's **/home/ron/Documents** instead of **/documents**

Do you come from a Windows background? If so, it's like the difference between **C:\Documents** and **C:\Documents and Settings\ron\Documents**

Copy and paste this command into the terminal. Note that everything's case-sensitive--lowercase *documents* won't work: ```
sudo chown -R ron:ron /home/ron/Documents
```

---

### Post by Hotwhlz85 on 2006-07-14
And yes I come from a loooooooooooooooooooong Windows background.  It shows huh?  That fixed it!!!

Now to do the same to that My documents folder and get rid of it.

Thanks for all the help and for hanging in there with me, it's VERY much appreciated.

Ron

---

### Post by aysiu on 2006-07-14
Just a tip for the future: the slash in there makes a big difference. ```
cd /Documents
``` means that you want to go into the Documents directory from the top-level directory. ```
cd Documents
``` means you want to go into the Documents directory that's underneath whatever directory you're in right now.

It's actually no different from... well, not Windows, but DOS, anyway.

---

### Post by Hotwhlz85 on 2006-07-15
One final thing for the night...I rebooted into Windows to move my music files over to the Documents folder you just helped me with.  When I booted back into Ubuntu the folder was once again locked.  I tried the chown command again without success so I went to disk manager and the label was set to "none" again.  I changed it back to /home/ron/Documents and it would open.

Hopefully this won't be an every time thing.

Thanks again for all your help aysiu.

Ron

---

### Post by aysiu on 2006-07-15
Wait... is this a Windows partition? If so, it's not about *chown*ing. It's about mounting.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Hotwhlz85 on 2006-07-15
No, at least it's not meant to be.  I used the FS-Drive program I read about on your site to get Windows to read and write to ext3 files. The partition is an ext3 partition though.  

If I could figure out how to do a screenshot of Gparted showing my partitions it might make more sense.  Here's how I did it though.

Sda1 is 7 Gb and has the hidden system restore files for Windows that are used in place of a recovery cd.
Sda2 is 50 Gb and is an NTFS partition for Windows.
Sda3 is 50 Gb and is an ext3 and is the /root
Sda6 is 140 Gb and is the partition I have been fighting all night. 
Then the swap partition is about 2 Gb.

I tried naming Sda6 /home but it never would work.  When I changed it to /home/ron/Documents it would let me enable it and I could open it and write to it then.

Have I configured that partition wrong?

Ron

---

### Post by Hotwhlz85 on 2006-07-15
I checked the link you sent about mounting and tried the fdisk command.  Here's what I got:

[IMG]http://www.carolinadreamin.net/KC/Screenshot-1.png[/IMG]

Ron

---

### Post by aysiu on 2006-07-15
Can you post the output of these three commands, and I'll get a better sense of what's going on? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Oh, I just saw your last post. That's supposed to be a lowercase L, not the number one.

P.S. You can highlight text from the terminal and copy and paste it into posts--might be faster than uploading screenshots of your terminal.

---

### Post by Hotwhlz85 on 2006-07-15
From looking at the mount points I think I have a royal mess!

---

### Post by Hotwhlz85 on 2006-07-15
Thanks, the cut and paste IS much easier.  

Here's the result of what you just asked for:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         914     7341673+  12  Compaq diagnostics
/dev/sda2   *         915        7313    51399967+   7  HPFS/NTFS
/dev/sda3            7314       13718    51448162+  83  Linux
/dev/sda4           13719       30401   134006197+   f  W95 Ext'd (LBA)
/dev/sda5           30027       30401     3012156   82  Linux swap / Solaris
/dev/sda6           13719       30026   130993947   83  Linux

Partition table entries are not in disk order
ron@ron-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              49G  2.6G   44G   6% /
varrun                502M   80K  502M   1% /var/run
varlock               502M  4.0K  502M   1% /var/lock
udev                  502M  144K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   19M  484M   4% /lib/modules/2.6.15-26-386/volatile
/dev/sda1             7.1G  4.1G  3.0G  59% /tmp/disks-conf-sda1
/dev/sda2              50G   20G   30G  40% /tmp/disks-conf-sda2
/dev/sda6             123G  2.0G  115G   2% /home/ron/Documents
ron@ron-desktop:~$ cat /etc/fstab

---

### Post by aysiu on 2006-07-15
Can you hit **Enter** after that last command (*cat /etc/fstab*)?

---

### Post by Hotwhlz85 on 2006-07-15
Duhhh.  Sorry about that.

Here ya go:

ron@ron-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
ron@ron-desktop:~$

---

### Post by aysiu on 2006-07-15
So the documents folder isn't in your /etc/fstab. Well, I think putting it in there may solve your problem.

Copy (Control-C) and paste (Shift-Insert) these commands into the terminal. It's faster than retyping, and it's less likely you'll mistype something: ```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
``` This will open up Gedit with root privileges. If you see warnings or "errors," just ignore them. In the new text document, add this line: ```
/dev/sda6 /home/ron/Documents ext3 defaults 0 0
``` So your final /etc/fstab should look like this: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda6 /home/ron/Documents ext3 defaults 0 0
``` Save and exit Gedit. Then ```
sudo mount -a
sudo chown -R ron:ron /home/ron/Documents
``` You should be good from now on.

---

### Post by Hotwhlz85 on 2006-07-15
Or at least until the next time ...  :)

aysiu I can't thank you enough for your patience and your help.  People like you are what makes these forums great.  My hat is off to you sir.

With great appreciation,
Ron

---

