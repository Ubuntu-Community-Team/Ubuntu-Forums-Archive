---
title: "[SOLVED] Creating new /home"
date: 2009-01-01
forum: General Help
---

### Post by Schok on 2009-01-01
i installed ubuntu 8.10 on a 10gb partition. now i have 1 ext3 partition (20gb) free of space and it is named /media. How do i convert it into /home? cause my / is getting full..

here are some info which might be useful:
/media = /dev/sda3
ubuntu = /dev/sda4   --->  /  = /dev/sda5
                          swap= /dev/sda6


sry for the noob question, im kinda new in this partitioning field..

---

### Post by nemilar on 2009-01-01
can you post the output of:

```
cat /etc/fstab
```

---

### Post by Schok on 2009-01-01
cat /etc/fstab=

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7212c715-2344-4709-bea4-0be0546781ae /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2b994c09-0b8f-4cfa-94dd-0b3d3a538246 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Schok on 2009-01-01
and will ubuntu recognize the new /home after ive created it? will it transfer all the data from the current /home to the new one?

---

### Post by logos34 on 2009-01-01
Try the separate /home howto link in my signature.  You can use Gparted on the ubuntu live cd (system>admin>partition editor) to shrink / and make new ext3 /home.

You can use '/dev/sdxy' format as in the link, or 'UUID='.  To find the randomly-generated UUID for the new /home partition, do

sudo blkid

and add that to new /home fstab entry

---

### Post by Schok on 2009-01-02
ive followed the guide on ur link but when i log out and tried to login as root, it says that i can't login thru there even though i pressed alt+F1(don't know whats that for..)
so then i tried this method under the comments column:-

regarding to "login as root"
Submitted by makl (not verified) on Fri, 09/12/2008 - 23:32.

regarding to "login as root" just do like this example

hannah@pysen:~$ sudo passwd root
Enter new UNIX password: [passwd of your choice]
Retype new UNIX password:
passwd: password updated successfully

then su as root

hannah@pysen:~$ su -
Password:
root@pysen:~#
done!

Matti



and then i followed the guide thru the terminal but it showed this:

gomez@MAHA617:~$ su -
Password: 
root@MAHA617:~# mv /home /home.bak
root@MAHA617:~# mkdir /home
root@MAHA617:~# mount -t ext3 /dev/sda3 /home
root@MAHA617:~# cp -a /home.bak/* /home
cp: cannot stat `/home.bak/gomez/.gvfs': Permission denied
root@MAHA617:~# 


what should i do?

---

### Post by logos34 on 2009-01-02
something happened when you changed the passwd--didn't need to do that, only log in to root shell! (a simple 'sudo -i' would have been enough).  

did everything else copy, or did the .gvfs permission error bring it to a halt? 

If everything else copied, I think you can just make a new .gvfs if necessary in the new /home.  

Otherwise, unmount sda3, move 'home.bak' to /home, log out of desktop and then log back in with new password...then try again

edit: I just did a test and I get the error too...no big deal...it's just an tmp folder for gnome virtual file system--you can make a new one if necessary

---

### Post by Schok on 2009-01-02
well i stopped right there in case i was doing something wrong. how do i make a new .gvfs? 

anyways now i cant find sda3 through the file browser, but i can see it in the gparted and its mounted as /home. does that mean ive done it?

oh and i havent done the last part of the guide yet, which is:

Open your /etc/fstab file, and add this line, in my case it is /dev/sda3 but could be different for you.

/dev/sda3       /home           ext3    defaults,errors=remount-ro 0    1


When i wanted to save the file it says i do not have permission..how do i run as it as admin?

---

### Post by logos34 on 2009-01-02
sorry for not responding earlier

to open with root privileges:

**gksudo** gedit /etc/fstab

add the line for /home, save and close

reboot

if no .gvfs folder is created automatically, make a new one:

mkdir .gvfs
sudo chown -R user:user .gvfs (where 'user' = your user name)
sudo chmod -R 700 .gvfs

---

### Post by Schok on 2009-01-02
hey thanks! i think it worked. for the gvfs i didnt know it was hidden, then i found it. lol thanks again, mate

---

### Post by logos34 on 2009-01-02
no prob.  my pleasure.

In case you're interested, I found out a little more about that '.gfvs': it's apparently some type of virtual filesystem in Gnome involving fuse (it replaces gnome-vfs)--i.e. basically just an empty mountpoint--with a [couple of oddities and at least one bug associated with it]("http://ubuntuforums.org/showthread.php?t=791693").  But you can ignore it, Gnome should recreate it automatically as needed.   

All we had to do is use the '--exclude=' option to ignore it, as [described here]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

anyway good luck and enjoy

if it by chance complains about .dmrc or whatnot at login, there's [this tip]("http://www.psychocats.net/ubuntu/separatehome#troubleshooting").

---

### Post by logos34 on 2009-01-02
[double paste-deleted]

---

