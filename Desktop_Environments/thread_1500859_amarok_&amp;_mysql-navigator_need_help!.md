---
title: "amarok &amp; mysql-navigator: need help!"
date: 2010-06-03
forum: Desktop Environments
---

### Post by chitowner2 on 2010-06-03
OK so I got my music collection into mySQL and got amarok config changed to use it. I then installed mysql-navigator and got navigator to run.

My goal is to access a table listing all tracks in the collection including title, album, artist, size and playtime (minutes:seconds) as parameters, and then make changes based on sorting those attributes. Specifically, I want to delete empty tracks.

Amarok used to have a "clear bad or empty tracks" option, but in 2.2 that option seems to be missing.

There are two immediate problems with navigator: first, none of the tables list more than 100 rows and I do not see any way to step through or increase table length beyond 100 rows. this seems a ludicrous limitation, so I am sure there must be a way to see the rest. 

Second, although I find a "playlist-tracks" table listed, it is empty, and I see no way of populating it.

Anybody know this stuff? I've already spent hours searching through web pages and found nothing that helps. I can't even find a manual for navigator!  :confused:

Thanks,
CT

---

### Post by chowanec on 2010-06-13
With the 100 record limitation -- you can change that to whatever you want.  Go to Tools -> Options and change the "Query limit" from 0 - 100 to 0 - <whatever you want>.

Straightforward enough.  The second bit, I can't help you with. :P

---

