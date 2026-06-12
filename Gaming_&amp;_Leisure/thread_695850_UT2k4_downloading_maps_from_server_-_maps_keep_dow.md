---
title: "UT2k4 downloading maps from server - maps keep downloading"
date: 2008-02-13
forum: Gaming &amp; Leisure
---

### Post by fprintf on 2008-02-13
Thanks to everyone who posted questions and answers on installing UT2004, I have finally gotten my copy of the game working on my Linux partition (I have been playing on Windows for 9 months now).

However, when I go to my favorite sniping server the available maps will download quickly once to 100%, and then will immediately reset and start downloading again, though more slowly this time. I never actually get to play the maps because I seem to be stuck in a loop.

I have checked my permissions on my Cache folder and they are:

user@user-desktop:~$ ls -l .ut2004
total 3920
drwxrwxr-- 2 user user    4096 2008-02-13 11:56 Cache
-rw-r--r-- 1 user user 4001792 2008-02-13 13:13 Cache0002.tmp
drwxrwxr-- 2 user user    4096 2008-02-13 13:03 System
user@user-desktop:~$

Any ideas why the maps won't download all the way and let me play them? I was thinking the maps just aren't being saved to the folder. My regular /usr/local/games/ut2004/cache is basically the same except the last two digits of the permissions are wx instead of -- .

p.s. I know I should probably not have 777 for everything. Thoughts on which one to use would be appreciated also.

---

### Post by FrozenFox on 2008-02-13
Have you tried a different server? That's typically a bug with the server's map setup: the map filesize/version on the ut2004 server do not match with the map that is pointed to on the public redirect (download server) the ut2004 server is using to speed up downloads, which happens regardless of OS. When you dl it fast the first time it's saved then probably deleted when the redirect and the map attempted to be loaded from the ut2004 server (and your pc) do not match up in favor of the slow-downloading one which you cancel. You may have just downloaded most of those maps on windows before the redirect and the server you are going to lost synchronization. If you can dl maps from some other server, then it is highly unlikely to be a ut2004/linux/permissions issue, but the fault of the server. If you have issues dling elsewhere (try a random onslaught server not on a default map), please tell us and we will try to figure out something further. If you still have windows installed and it is indeed a synchronization problem between the server and redirect, you could easily move your maps folder over to your linux ut2004 setup in that folder you mentioned, .ut2004, but check other servers first.

---

### Post by fprintf on 2008-02-13
Thanks for the quick response.

I tried several other servers just now, and I am having the same issue with all of them. Onslaught, deathmatch, you name it.

I do know what you are saying about moving the maps over, and since I have UT2k3mi I can definitely pull the maps out of my cache for my usual. And yet occasionally I will need to download a new map if I join a new server. So I'd ideally like to get it working.

Thanks,
Fprintf

---

### Post by FrozenFox on 2008-02-13
Hehe, indeed, I intended to say only to copy the maps over if it's just a problem with that one server, not to use it for all of them. That would be a total pain and you might as well just run it in wine in such a case X_X.

Hrmmm.. let's see what else could potentially be wrong..

slot 0 is what kind of file is it (file(-), (d)irectory, (l)ink, whatnot). next 3 are permissions for the owner, next 3 for the group, next 3 for others.. (r)ead, (w)rite, e(x)ecute.

My settings that work fine on hardy with the newest patch (via the mega pack thingo from loki, iirc) are

$ ls -l /home/fox/.ut2004
total 32
drwx------ 2 fox fox 4096 2008-02-07 21:35 Cache
drwxr-xr-x 2 fox fox 4096 2008-02-04 00:07 Custom
drwxr-xr-x 2 fox fox 4096 2007-12-27 15:21 Demos
drwxr-xr-x 2 fox fox 4096 2008-02-02 23:42 ScreenShots
drwxr-xr-x 2 fox fox 4096 2008-02-02 23:42 Sounds
drwx------ 2 fox fox 4096 2008-02-09 06:21 System
drwxr-xr-x 2 fox fox 4096 2008-02-02 23:41 Textures
drwx------ 2 fox fox 4096 2008-02-09 05:55 UserLogs

EDIT: I just noticed that your owner is set to "user". Is that your username? Somehow I don't think so, perhaps that's the issue.

If not, try sudo chown yourname::yourname -R /usr/local/games/ut2004/cache and sudo chown yourname::yourname -R /home/yourname/.ut2004

---

### Post by FrozenFox on 2008-02-13
Hehe, I edited the above post so much. Please check it again and try that..

---

### Post by fprintf on 2008-02-13
Thanks for all the help. I got it working by reinstalling the 3369 patch *after* installing the MegaPack download. I had not previously installed the MegaPack. I got this idea after reviewing the [http://gaming.gwos.org/doku.php/guides:64bit:ut2004](http://gaming.gwos.org/doku.php/guides:64bit:ut2004) guide to the UT installation. 

So now it works!  (safely downloading maps so far so good!)

---

### Post by FrozenFox on 2008-02-13
Good to hear! :)

---

