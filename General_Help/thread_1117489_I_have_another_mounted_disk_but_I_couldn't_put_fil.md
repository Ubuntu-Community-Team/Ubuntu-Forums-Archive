---
title: "I have another mounted disk but I couldn't put files in it"
date: 2009-04-06
forum: General Help
---

### Post by alcatraz678 on 2009-04-06
Hey guys, I divided my hard drive into 2 partitions and I'm trying to put some data into the 2nd partition but I got the following error:

[IMG]http://i708.photobucket.com/albums/ww89/rymngh/Screenshot.png[/IMG]

---

### Post by Cybie257 on 2009-04-06
go into terminal and type

    sudo chmod 777 /media/disk-1

try to copy files to it. Does it work? If so, it was just permissions. I have that issue every now and then. sometimes it defaults to working, other times it won't let me write to it until I set the permissions. 

Of course, the 777 gives everyone permissions, but you can adjust as needed after you use this for testing. 

-Cybie

---

### Post by alcatraz678 on 2009-04-06
Ok it worked! Thanks!

---

