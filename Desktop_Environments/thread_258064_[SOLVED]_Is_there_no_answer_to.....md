---
title: "[SOLVED] Is there no answer to...."
date: 2006-09-15
forum: Desktop Environments
---

### Post by Cariboo1938 on 2006-09-15
I wonder if there is no answer to my questions (below), or if the questions are not asked clearly enough. I placed them several times at the Ubuntu Forums and there was no reaction, not even a comment. What else could I do? I tried Linux.org Forums, Debian, Google ...without results.
> After installing "udftools" for "packet writing" I want to create a new mount point and mount a CD.

Here is what I do:
```
sudo mkdir -p /media/udf0
```
and then
```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0
```
After that I get the error message:
[QUOTE][COLOR="Red"]mount: /dev/pktcdvd/0: can't read superblock[/COLOR]
The measures I would have to take where originally posted by dradul  [View Post]("http://www.ubuntuforums.org/showpost.php?p=1476368&postcount=14")> 
You may need to [COLOR="Magenta"]disable the other, default, entries[/COLOR]. The message means that the CD has already been mounted as a read-only volume probably. You can solv it by setting the default entries to be "noauto" and using pmount to mount them as neded.[/QUOTE]

[B][COLOR="Blue"]What do I need to do?
Where can/must I "disable the other, default, entries"?[/COLOR][/B]
Please help, I don't know how to do it.
Any comment is very much appreciated!

---

### Post by jimbren on 2006-09-15
I can't help you, but I hope you understand that when a question goes unanswered, it's not because no one wants to help you out--they don't know the answer to your question and would prefer to not clutter up  your thread with useless "good luck with that" comments.

So, ah...good luck with that.

kisses,

jimbo

---

### Post by Cariboo1938 on 2006-09-15
> **jimbren said:**
> I can't help you, but I hope you understand that when a question goes unanswered, it's not because no one wants to help you out--they don't know the answer to your question and would prefer to not clutter up  your thread with useless "good luck with that" comments.
So, ah...good luck with that.
kisses,
jimboThank you for the comment...I'm glad you replied, because I already thought it is somethting wrong with me...Thanks](*,)  
Cariboo

---

### Post by master_b on 2006-09-15
Quote "Where can/must I "disable the other, default, entries"? End Quote

edit /etc/fstab - change the "auto" entry in the line for your cdrom to "noauto"

You will then have to mount your cdrom manually whenever you need to use it.

Hope thia helps

Bill

---

### Post by Cariboo1938 on 2006-09-17
> **master_b said:**
> Quote "Where can/must I "disable the other, default, entries"? End Quote

edit /etc/fstab - change the "auto" entry in the line for your cdrom to "noauto"
You will then have to mount your cdrom manually whenever you need to use it.
Hope thia helps
BillThanks Bill, 
I already did that but it didn't help. I still get the errror message when I try to mount the 'packet writing device'. Here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#<file system> <mount point>   <type>   <options>          <dump>  <pass>
## Linux 'Ubunu 6.06'
proc             /proc           proc     defaults             0       0
/dev/sda2        /                ext3    defaults,errors=remount-ro 0       1
/dev/sda3        /Storage         ext3    defaults             0       2
/dev/sda1        /boot            ext3    defaults             0       2
/dev/sda5        /home            ext3    defaults             0       2
/dev/sda6        /usr             ext3    defaults             0       2
/dev/sda7        /var             ext3    defaults             0       2
/dev/sda8        none             swap    sw                   0       0

#Normal disk device
/dev/hda      /media/cdrom1    iso9660,udf   rw,users,noauto       0      0
/dev/hdb      /media/cdvdrw    iso9660,udf   rw,users,noauto       0      0

#Packet writing device
/dev/pktcdvd/0  /media/udf0      udf    users,noauto,noatime,utf8  0      0
/dev/pktcdvd/1  /media/udf1      udf    users,noauto,noatime,utf8  0 0
```There must be another file responsable for automount because when I insert a CD it is mounted to the desktop immediately. It seems nobody had this problem yet or it was never solved.

Thanks again for your replies. I posted my question in different forums and I got only two replies so far...yours and jimbo's. Maybe we can work together to find a solution...maybe someone else has an idea what to do???
cheers
Cariboo

---

### Post by Cariboo1938 on 2006-09-18
:-\" I got it running...packet writing works...I can use my CD-r/w as a large storage device...My mistake was doing things and not exactly knowing what I do.
I had to mount a CD and not the CD drive, because the CD has the File System on it I wanted to use...UDF.
The solution is:
When executing the command
Code:
*sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/udf0*
the formatted CD has to be inserted in the corresponding drive!
[dradul's HowTo]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=dradul") works. 
I thank all of you for your participation helping me to solve the problem. Case closed!
Thanks again 
Cariboo

---

