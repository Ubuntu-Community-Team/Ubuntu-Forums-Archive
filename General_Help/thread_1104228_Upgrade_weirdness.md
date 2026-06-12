---
title: "Upgrade weirdness"
date: 2009-03-23
forum: General Help
---

### Post by jo4hnc on 2009-03-23
I upgraded from Hardy LTS to Intrepid last night. One aberration is that I get a message at bootup that it seems a number of folks have gotten regarding "aperture beyond 4gb". I realize that this is a bug and will follow up on that.

The stranger problem is that the first partition on my slave drive seems to be being recognized as a picture disk. There is a bar at the top when I open the disk that states "These files are on a picture CD". 

Additionally, The permissions tab for all drives, the slave with 2 partitions and an external USB drive with 3 partitions states that permissions on all could not be determined. I have used sudo nautilus to set the permissions on all of the drives with no effect. Despite the fact that when I open the properties of the drives in sudo the permissions are correct only on the slave drive.


I had to use the storage device manager to get the slave to mount. The external mounted automatically.

Should I use chown to reset the disks to regain ownership of the drive(s)? 

John C

AMD 64 3200 64
3GB RAM


Update: Tried changing permissions in both sudo and gksu also tried changing the owner of the disks in both. No Luck. Any ideas would be greatly appreciated.   j

---

### Post by jo4hnc on 2009-03-23
Well, guess I'm carrying on this conversation with myself(lol).

I finally was able to get permissions on the internal slave drive. I unplugged it, restarted the machine and then reconnected it. One partition still shows that it is a picture disk. This doesn't affect the use of the disk but it bugs me. One other thing that I find strange is that despite the fact that it is an internal drive when I drop down the "Places" menu it is shown as removable media. THis was not the case in Hardy.

On the external drive I cannot change the ownership from root. tried several ways using info from the forum. No luck at all. When I run nautilus under sudo or gksu and try to change the permissions and click on my name, the dropdown snaps back to root on all three partitions. Chown didn't work.

I can usually figure this stuff out but this one has me stumped.

j

---

### Post by rockstone on 2009-03-23
I believe the picture disk problem occurs when you have a folder named Pictures in the root folder of the drive. 

Not sure about the permissions problem. What happens when you try to use chown?

---

### Post by jo4hnc on 2009-03-23
I've tried chown a few times and nothing happens. Used jaycee(my user name)and jaycee:jaycee and neither worked.

Thanks for the tip on the pictures folder. I'll try changing the name. And thanks for the reply.

j

---

### Post by jo4hnc on 2009-03-23
Hey Rockstone,

I moved all files off of that partition, here weren't too many there but there were pictures in a folder named pictures. Unmounted and then remounted the partition and VIOLA!! no more picture cd reference. Thanks!

John

---

### Post by jo4hnc on 2009-03-23
Well, thanks to this post, I found out that I was spinning my wheels a bit. The external drive I was trying to set permissions on is a NTFS drive. A whole different kettle of fish! This is the post that gave me some direction.

[http://ubuntuforums.org/showthread.php?t=1104377](http://ubuntuforums.org/showthread.php?t=1104377)

---

