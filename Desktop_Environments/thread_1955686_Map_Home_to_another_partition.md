---
title: "Map Home to another partition"
date: 2012-04-09
forum: Desktop Environments
---

### Post by horusofoz on 2012-04-09
I have a laptop that my girlfriend and I share. I want to use Ubuntu but she is insistent on using Windows 7 herself. To resolve this I plan on dual booting with a third partition for data.

Can you please advise how I would go about mapping the Ubuntu Home Folder and it's subfolders to an identical folder structure on the third partition?

!!BONUS SUPER EXTRA QUESTION!!

Any idea how I would go about mapping the Windows 7 equivalent folders to the Ubuntu folder structure on the third partition?

A thousand thank yous to you who can help :) ;)

---

### Post by oldfred on 2012-04-09
I just copy all the folders like Music, Documents, Video etc to folders in the shared data partition. Then I link those folders back to my /home. Do not know about Windows.

I use linking, some others suggest bind. Some networking may work better with bind, but I use nfs and copy files from my laptop to my desktop & back without issue. But I use the mount point of the data partition not the links.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

You can also set your Windows (c drive) to be read only to avoid issues that may occur if writing into Windows. Either way with dual booting do not hibernate in either system as changes by the other system may corrupt the hibernation and therefore the whole system.

---

