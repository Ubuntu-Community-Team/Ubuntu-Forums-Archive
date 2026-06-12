---
title: "How can I clean up my Home folder?"
date: 2011-06-17
forum: Desktop Environments
---

### Post by pashlit on 2011-06-17
Hey there,
I have my HOME folder on a separate partition and I am dual booting. I have both Ubuntu 9.10 (still the best distro IMHO) and latest Ubuntu 11.04 sharing the same Home folder. I can see that HOME holder consists of so much stuff besides the main folders I use. I basically only need Pictures, Documents, Videos etc. folders. So can I just leave those folders and delete the rest? I guess there is so much junk accumulated for 3 years that might cause bugs and stuff. Basically I just want to do a fresh install but keep my main folders like Docs, Pics etc. So if I delete all the junk I dont need and do a fresh install will Ubuntu recreate the new system folders neended on my Home partition and leave Pics, Docs, Vids etc. folders untouched?
Thanks

---

### Post by oldfred on 2011-06-17
Your /home has two things, all your data and mostly in hidden files & folders all your USER configurations. If you delete the configs you may have major issues. Also in hidden folders are all your firefox & thunderbird data and other applications may have data folders also.

The hidden configs are actually pretty small. My /home is 1GB with 3/4 of that .wine with the windows version of Picasa. I have moved other hidden data folders like Firefox & Thunderbird to other partitions. I expect to move .wine eventually into my data partition also.

When I do a clean install I leave /home inside / (root). I may copy some config files from the old install to the new as I have both still installed, but I do then shared data partitions. Some Unix purists say it is more Windows like to have separate /data and it may not work if you have different distributions with different UIDs & GIDs or ownership issues.

---

### Post by pashlit on 2011-06-17
> **oldfred said:**
> Your /home has two things, all your data and mostly in hidden files & folders all your USER configurations. If you delete the configs you may have major issues. Also in hidden folders are all your firefox & thunderbird data and other applications may have data folders also.

The hidden configs are actually pretty small. My /home is 1GB with 3/4 of that .wine with the windows version of Picasa. I have moved other hidden data folders like Firefox & Thunderbird to other partitions. I expect to move .wine eventually into my data partition also.

When I do a clean install I leave /home inside / (root). I may copy some config files from the old install to the new as I have both still installed, but I do then shared data partitions. Some Unix purists say it is more Windows like to have separate /data and it may not work if you have different distributions with different UIDs & GIDs or ownership issues.

I dont use Thunderbird and I dont need any other configs besides may be Picasa and Ekiga. The rest can go. May be it is my imagination but I have a feeling that when I reinstall the distro it has much more bugs if I leave all the old config and other files in Home folder.Please correct me if I am wrong.
I have always admired completely new fresh install but I dont want to copy a back up of my Pics, Docs, Music and Vids (72 gigs and counting!!) every time I decide to reinstall the system.

---

### Post by oldfred on 2011-06-17
That is exactly why I use a data partition and link my data folders into my /home.

I have some data in a shared NTFS partition, originally for sharing with XP which I now use rarely. And /data which has all the standard folders from Ubuntu plus a few I have added.

Shared /data -see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

---

### Post by pashlit on 2011-06-17
> **oldfred said:**
> That is exactly why I use a data partition and link my data folders into my /home.

I have some data in a shared NTFS partition, originally for sharing with XP which I now use rarely. And /data which has all the standard folders from Ubuntu plus a few I have added.

Shared /data -see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

Thanks a bunch. Thats a lot of good and confusing stuff :P
Basically my goal was to keep my Docs, Pics, Music etc data separately. Then after installing new distro(s) I d like to just link those folders to distro's home folders. But I dont quite know how to keep the configs for Pictures and Music so new system could see and recognize them correctly. I use Picasa and would prefer it to see all those linked folders. I just went with keeping Home folder on separate partition but found that method being not that good cause, as I had mentioned, there are lots of garbage left from old systems and every time I  switch from 9.10 to 11.04 I have to reconfigure desktop settings that might mess the whole system completely. I was reading lots of info on how to ideally organize data and share it among different distros but didnt find any decent solution. :confused:
To put that short: I just want my Docs, Pics, Music, Vids ets separetely with the ability to keep sync settings and configs for progs like Picasa. To tell the truth I dont quite understand the concept Linux uses. Why does it keep data and settings all together in one Home folder??? To me Home folder is just a data folder. Why would I keep other system stuff in there?

---

### Post by oldfred on 2011-06-17
It is set up as a multi-user system. Each users has his own data and user configuration setting in his own /home. 

I currently reinstall Picasa so it has to find all my photos on reinstall. That is why I want to move .wine with my windows Picasa into my /data partition. Every thing else is remounted in each new install and in the same place in my portable. After doing the mounting and linking manually, I quickly realized I was redoing the same thing over & over. I then just listed history and copied all the commands into a bash file (some cleanup required).

---

