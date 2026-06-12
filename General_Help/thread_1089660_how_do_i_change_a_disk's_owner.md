---
title: "how do i change a disk's owner?"
date: 2009-03-07
forum: General Help
---

### Post by chriskin on 2009-03-07
i would like to change the owner of an external drive from root to myself
how can it be done?
(the graphical way of right click properties and changing it has a problem-the moment i change it from root to myself, it changes back by itself)

---

### Post by hexanol on 2009-03-07
What kind of file-system the external drive holds ? FAT ?

---

### Post by chriskin on 2009-03-07
ntfs

---

### Post by hexanol on 2009-03-07
Then, it's done while mounting the file-system. Basically, you need to specify the uid option. Something like

```
$ sudo mount -t ntfs-3g -o uid=*your_uid* /dev/sd*XX* */somewhere* 
```

For more info, look at "man mount" and search for the word "ntfs". If you don't know how to search with man, read the man page for man! :D

---

### Post by chriskin on 2009-03-07
can you explain what i should write at the uid thing?
i use the  sudo mount -t ntfs-3g /dev/sdb1 /media/disk command but it makes root the owner, not me

---

### Post by |Porsche on 2009-03-07
Open a terminal and type ```
id
```

You will see something that says uid=####, where #### are some numbers. That is your uid(user id).

Your command should look like this
```
sudo mount -t ntfs-3g -o uid=#### /dev/sdXX /somewhere
```

---

### Post by chriskin on 2009-03-07
i found it
thank you, i am going to try it now

---

### Post by tommcd on 2009-03-07
Try reading this article for more info:
[http://www.swerdna.net.au/linhowtontfs.html](http://www.swerdna.net.au/linhowtontfs.html)
It explains how to add your ntfs partition to /etc/fstab si it can be automatically mounted.

---

### Post by chriskin on 2009-03-07
it is automatically mounted, just for root as user instead of me

---

### Post by Nano_ext3 on 2009-03-07
I personally would just mount it with the proper user name and password.  Im assuming this is a drive or partition internal to your system and not a samba or windows share?  If its internal to your PC, there should be no issue what so ever in doing what you need to do to that drive.  Follow the other suggestion above if you wish, or you may do a chmod command on the folder you made inside /mnt as wel..

Please let us know how you made out!

Cheers 

-nano

---

### Post by chriskin on 2009-03-07
i tried the command given by porsche but the owner is still root, can someone give me another way?

as for the reason
it is not that i do not have permissions to use it once mounted, it is that i do not have the permission to mount and unmount it graphically. and this is kind of annoying as i have to unplug the drive every some hours to move it to another computer(it is an external one)

---

### Post by chriskin on 2009-03-07
> **Nano_ext3 said:**
> I personally would just mount it with the proper user name and password.  Im assuming this is a drive or partition internal to your system and not a samba or windows share?  If its internal to your PC, there should be no issue what so ever in doing what you need to do to that drive.  Follow the other suggestion above if you wish, [B]or you may do a chmod command on the folder you made inside /mnt as wel..
[/B] 
Please let us know how you made out!

Cheers 

-nano

can you make it a little clearer on how i can do this please?
everything else fails , root is still the owner

---

### Post by miegiel on 2009-03-07
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod) :twisted:

---

### Post by chriskin on 2009-03-07
nice, thanks for...eh...helping...

i will try to find some answer

---

### Post by miegiel on 2009-03-08
If there is a line in /etc/fstab to auto mount the partition during boot you can set the owner there (man and google can tell you more about fstab). You can also put a # at the start of the line in fstab to stop it from mounting that partition so that you can mount it manually.

---

