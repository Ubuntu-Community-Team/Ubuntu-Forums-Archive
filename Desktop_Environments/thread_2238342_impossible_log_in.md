---
title: "impossible log in"
date: 2014-08-07
forum: Desktop Environments
---

### Post by ciaps on 2014-08-07
Hi everyone,
this is my first post so I hope I'm in the right section and I'll be clear enough to explain the problem I have with my Ubuntu 14.04.1 LTS x86_64 (xubuntu desktop). 
Right now I'm logged in as guest on my laptop because I can't log in with my normal user. When I wright my password and press Enter I get a black screen for like two seconds and then back again the window for logging in. 
Here what I did to get this issue.
I wanted to install Celtx and followed the procedure that I found [_here_]("http://ubuntuhandbook.org/index.php/2013/07/install-celtx-2-9-7-ubuntu-linux/"). 

Probably the big mistake has been installing the required repository:```
[COLOR=#333333][FONT=Monaco]sudo apt-get install gnome-panel --no-install-recommends[/FONT][/COLOR]
```
Did it all until the end and got a system error message about the desktop (I cannot recall the exact words) and my home directory was gone. I thought reboot was going to solve it but now I can't log in anymore with my user.
I've already tried to reboot and press Ctrl+Alt+t when asked for my password but the terminal doesn't show up. 
How can I get in again with my normal user and fix the problem I caused?
Many thanks to all of you guys for your attention and help.

---

### Post by oldfred on 2014-08-07
I install full gnome-panel and do not have issues with that.
I think they want gnome-panel as then the procedure to create a icon is based on that not Unity.

       Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)

You can try the reset password procedure.

 [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)


Is your /home inside / (root) or a separate partition. 
If separate partition perhaps it has corruption and needs fsck?

      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by ciaps on 2014-08-07
Hi, thanx for helping me.
My /home is in /. I do have different partitions that I'm not able to open as guest for lack of privileges.
Finally I got the terminal working to log in with Ctrl+Alt+F1, but I got this line back: "No directory, logging in with HOME=/"
I don't think it's a matter of password but if I can't do anything else I'll give it a try.

---

### Post by ciaps on 2014-08-07
Also the line ```
ls /home
``` gave nothing back.

---

### Post by ajgreeny on 2014-08-07
> **ciaps said:**
> Also the line ```
ls /home
``` gave nothing back.
That is not good!

Can you boot to a live system and mount the installed version of Ubuntu, then look inside /home using nautilus to see if anything is there, or again run the ls -l command in terminal, only this time it will be```
ls -l /media/ubuntu/[COLOR=#ff0000]*partiton-name*[/COLOR]/home
```You will just have to look to see what the [COLOR=#ff0000]*partition-name*[/COLOR] is as there is no way we can tell how it will be named when mounted.

---

### Post by ciaps on 2014-08-07
Thanks for your answer, I have to leave now but I'll try it later. Uffh, I thought it would have been easier:(

---

### Post by ajgreeny on 2014-08-07
It may end up being quite easy to put right, but until we know what is actually in /home we can't go any further.

The guest account you were using, which is not something I have ever used on my system, has very limited permissions and that fact may limit what you can see in the /home folder when using that.

---

### Post by ciaps on 2014-08-08
Finally I could boot a live session from dvd. 
Searching in the partition where my installed xubuntu is, I found this: 
[ATTACH=CONFIG]255316[/ATTACH][ATTACH=CONFIG]255317[/ATTACH]

But when I enetered the command ls -l, I got:
```
xubuntu@xubuntu:~/Desktop$ ls -l /media/xubuntu/
total 4
drwxr-xr-x 25 root root 4096 Aug  6 15:38 GNU linux
```
And then:
```
xubuntu@xubuntu:~/Desktop$ ls -l /media/xubuntu/GNU linux/
ls: cannot access /media/xubuntu/GNU: No such file or directory
ls: cannot access linux/: No such file or directory
```
Why can't I access my GNU linux directory?

---

### Post by coffeecat on 2014-08-08
You have a space in "GNU linux" that needs to be escaped:

```
ls -l /media/xubuntu/GNU\ linux/
```

---

### Post by ciaps on 2014-08-08
Thanks.Here's the result:
```
xubuntu@xubuntu:~/Desktop$ ls -l /media/xubuntu/GNU\ linux/
total 116
drwxr-xr-x   2 root root  4096 Jul 24 06:14 bin
drwxr-xr-x   3 root root  4096 Aug  6 15:19 boot
drwxr-xr-x   2 root root  4096 Oct 31  2013 cdrom
drwxr-xr-x   4 root root  4096 Oct 16  2013 dev
drwxr-xr-x 150 root root 12288 Aug  8 10:40 etc
drwxr-xr-x   2 root root  4096 Aug  6 15:46 home
lrwxrwxrwx   1 root root    33 Jul 17 22:55 initrd.img -> boot/initrd.img-3.13.0-32-generic
lrwxrwxrwx   1 root root    33 Jun 26 06:14 initrd.img.old -> boot/initrd.img-3.13.0-30-generic
drwxr-xr-x  24 root root  4096 Aug  5 07:06 lib
drwxr-xr-x   2 root root  4096 Aug  5 07:06 lib32
drwxr-xr-x   2 root root  4096 Aug  5 07:06 lib64
drwx------   2 root root 16384 Oct 31  2013 lost+found
drwxr-xr-x   5 root root  4096 Aug  8 10:40 media
drwxr-xr-x   2 root root  4096 Oct 13  2013 mnt
drwxr-xr-x   5 root root  4096 Aug  5 16:09 opt
drwxr-xr-x   2 root root  4096 Oct 13  2013 proc
drwx------   5 root root  4096 Aug  6 15:47 root
drwxr-xr-x  12 root root  4096 Oct 16  2013 run
drwxr-xr-x   2 root root 12288 Aug  5 07:06 sbin
drwxr-xr-x   2 root root  4096 Oct 16  2013 srv
drwxr-xr-x   2 root root  4096 Jun  4  2013 sys
drwxrwxrwt   4 root root  4096 Aug  8 10:40 tmp
drwxr-xr-x  11 root root  4096 May 15 06:45 usr
drwxr-xr-x  14 root root  4096 Oct 31  2013 var
lrwxrwxrwx   1 root root    30 Jul 17 22:55 vmlinuz -> boot/vmlinuz-3.13.0-32-generic
lrwxrwxrwx   1 root root    30 Jun 26 06:14 vmlinuz.old -> boot/vmlinuz-3.13.0-30-generic

```
And then: 
```
xubuntu@xubuntu:~/Desktop$ ls -l /media/xubuntu/GNU\ linux/home
total 0
```

---

### Post by ciaps on 2014-08-08
> #From liveDVD/Flash so everything is unmounted,swap off if necessary,  change example shown with partition sdb1 to your partition(s) #e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required sudo e2fsck -C0 -p -f -v /dev/sdb1 #if errors: -y auto answers yes for fixes needing response, also see man e2fsck sudo e2fsck -f -y -v /dev/sdb1
@Oldfred: here's what you asked me to do earlier:
```
xubuntu@xubuntu:~/Desktop$ sudo e2fsck -C0 -p -f -v /dev/sda3
                                                                               
      379681 inodes used (11.85%, out of 3203072)
        1583 non-contiguous files (0.4%)
         695 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 307129/182/1
     2927950 blocks used (22.87%, out of 12800048)
           0 bad blocks
           1 large file

      262110 regular files
       38229 directories
          57 character device files
          25 block device files
           0 fifos
          26 links
       79249 symbolic links (72277 fast symbolic links)
           2 sockets
------------
      379698 files
```
and:
```
xubuntu@xubuntu:~/Desktop$ sudo e2fsck -f -y -v /dev/sda3
e2fsck 1.42.8 (20-Jun-2013)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      379681 inodes used (11.85%, out of 3203072)
        1583 non-contiguous files (0.4%)
         695 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 307129/182/1
     2927950 blocks used (22.87%, out of 12800048)
           0 bad blocks
           1 large file

      262110 regular files
       38229 directories
          57 character device files
          25 block device files
           0 fifos
          26 links
       79249 symbolic links (72277 fast symbolic links)
           2 sockets
------------
      379698 files
```

---

### Post by ciaps on 2014-08-09
I tried to reboot and when I got the log in window I used the terminal to get in.
Then I tried with:
[COLOR=#555555][FONT=Monaco]sudo mkdir /home/myusername[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]sudo reboot
[/FONT][/COLOR]But the next reboot nothing changed and I couldn't log in.
Anyone who knows what else I should try with?

---

### Post by ciaps on 2014-08-10
Looking in a blog I found a command to reset the gnome settings to defaults. It's quite old and I don't know if it can work on my xubuntu 14.04.
Once I get the log in screen I hit Ctrl+Alt+F1 for terminal and enter the line:
```
**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**
``` 
Then, to get back to my GUI desktop, I should hit Ctrl+Alt+F7.
I'm quite ignorant so don't Know whether I'm going to get things even worst or solve the problem.
Any suggestions?

---

### Post by steeldriver on 2014-08-10
> **ciaps said:**
> I tried to reboot and when I got the log in window I used the terminal to get in.
Then I tried with:
[COLOR=#555555][FONT=Monaco]sudo mkdir /home/myusername[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]sudo reboot
[/FONT][/COLOR]But the next reboot nothing changed and I couldn't log in.
Anyone who knows what else I should try with?

I haven't read through the whole thread, but if you are trying to  resolve this by creating a new home directory, you will need to give  that directory the correct ownership as well

```

sudo chown myusername:myusername /home/myusername

```

You should also check that the home directory is set accordingly in the passwd database

```

getent passwd myusername

```

---

### Post by ciaps on 2014-08-10
@steeldriver: do you think I still have a chance to have my /home directory in my system?
I booted a live-session from dvd and looked into the partition where my xubuntu is and found this:
```
[COLOR=#000000][FONT=Ubuntu Mono]xubuntu@xubuntu:~/Desktop$ ls -l /media/xubuntu/GNU\ linux/home
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]total 0[/FONT][/COLOR]
```
Facing the reality, if it says there's nothing in there, probably it's right...

---

### Post by steeldriver on 2014-08-10
Are you sure your home directory wasn't on a separate partition? look in the fstab file for any entries about 'home'

```

cat /media/xubuntu/GNU\ linux/etc/fstab

```

and check for any other possible partitions with

```

sudo parted -l

```

It's also possible that you moved the contents somewhere - you could use the 'find' command to search for them e.g.

```

sudo find /media/xubuntu/GNU\ linux/ -maxdepth 4 -user *myusername*

```

(you can use Ctrl-C to stop it if the wait gets too long)

---

### Post by ciaps on 2014-08-10
> Are you sure your home directory wasn't on a separate partition? look in the fstab file for any entries about 'home'

 	Code:
 	cat /media/xubuntu/GNU\ linux/etc/fstab 
and check for any other possible partitions with

 	Code:
 	sudo parted -l 
It's also possible that you moved the contents somewhere - you could use the 'find' command to search for them e.g.

 	Code:
 	sudo find /media/xubuntu/GNU\ linux/ -maxdepth 4 -user *myusername* 


Here are the results from the last suggestions:

```
xubuntu@xubuntu:~/Desktop$ cat /media/xubuntu/GNU\ linux/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=8000ab11-6daa-4ace-aabd-bd2f48993639 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b2f4950b-a0c2-451c-96c8-46e7184c9f56 none            swap    sw              0       0


```

```
xubuntu@xubuntu:~/Desktop$ sudo parted -l
Model: ATA HITACHI HTS72503 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  1262MB  1262MB  primary   ntfs
 2      1262MB  106GB   105GB   primary   ntfs
 3      106GB   159GB   52.4GB  primary   ext4            boot
 4      159GB   320GB   162GB   extended
 5      159GB   303GB   144GB   logical   fat32
 6      303GB   320GB   17.3GB  logical   linux-swap(v1)
```

```
xubuntu@xubuntu:~/Desktop$ sudo find /media/xubuntu/GNU\ linux/ -maxdepth 4 -user cristian
find: `cristian' is not the name of a known user
```

---

### Post by steeldriver on 2014-08-10
oops my bad - I guess 'find -user' isn't going to work from a live DVD, you would need to boot the broken system and log in at the Ctrl-Alt-F1 terminal again, then do

```

sudo find / -maxdepth 4 -user myusername

```

(possibly you could use 'find **-uid**' from the live DVD - you'd need to look up your uid value in the /media/xubuntu/GNU\ linux/etc/passwd file first though)

---

### Post by ciaps on 2014-08-10
> [COLOR=#000000][FONT=Ubuntu Mono]sudo find / -maxdepth 4 -user myusername[/FONT][/COLOR]

Done this and I found out my personal directory (home) is here: /usr/share/**cristian**/
All my stuff is still there!!!
Do you know how to put it back in the right place either from live-session or from terminal in the broken system?

---

### Post by steeldriver on 2014-08-10
If you have enough disk space to temporarily duplicate the contents, you should be able to do

```

sudo mkdir -p /home/cristian    # <--- just in case you didn't already do this

sudo cp -r /usr/share/cristian/* /home/cristian/

sudo chown -R cristian:cristian /home/cristian/

```

from the Ctrl-Alt-F1 terminal where you're already logged in as 'cristian', then reboot. Once you're sure everything's back to normal, you can delete the duplicate directory from /usr/share.

If you don't have space to do that, and you haven't added any files  since re-creating the /home/cristian directory, you can **boot the broken system into recovery mode** and then at the root prompt **#** do a straight  move

```

mv /usr/share/cristian/ /home/cristian/

chown -R cristian:cristian /home/cristian/

```

OTOH if you are more comfortable with the GUI, boot up your live DVD and then run

```

gksudo nautilus

```

from a terminal, which should allow you to drag'n'drop the contents back to their correct location and reset their ownership.

---

### Post by ciaps on 2014-08-10
> [COLOR=#000000][FONT=Ubuntu Mono]sudo mkdir -p /home/cristian    # <--- just in case you didn't already do this[/FONT][/COLOR]
I already did this:
```
[COLOR=#555555][FONT=Monaco]sudo mkdir /home/cristian[/FONT][/COLOR]
```
So just the '-p' is missing, don't know if it's essential...anyway the directory /cristian is already there...empty of course.

---

### Post by ciaps on 2014-08-12
> **steeldriver said:**
> If you have enough disk space to temporarily duplicate the contents, you should be able to do

```

sudo mkdir -p /home/cristian    # <--- just in case you didn't already do this

sudo cp -r /usr/share/cristian/* /home/cristian/

sudo chown -R cristian:cristian /home/cristian/

```

from the Ctrl-Alt-F1 terminal where you're already logged in as 'cristian', then reboot. Once you're sure everything's back to normal, you can delete the duplicate directory from /usr/share.

If you don't have space to do that, and you haven't added any files  since re-creating the /home/cristian directory, you can **boot the broken system into recovery mode** and then at the root prompt **#** do a straight  move

```

mv /usr/share/cristian/ /home/cristian/

chown -R cristian:cristian /home/cristian/

```

OTOH if you are more comfortable with the GUI, boot up your live DVD and then run

```

gksudo nautilus

```

from a terminal, which should allow you to drag'n'drop the contents back to their correct location and reset their ownership.

I followed your first solution and everything seems to work just fine: I'm now able to log in again with my normal user. I had to reset some stuff of my old desktop, such as wallpaper, themes, fonts, etc. but not a big a deal.
Thank you so much for your help and to everyone else who helped me solving my problem.

---

