---
title: "Amarok collections and samba"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Cyfr on 2006-06-12
Hi, I have sucessfully mounted a samba share from my server into /home/username/music

I manualy access the music from there, and I can even play the files directly in amarok.

However, when I try and build a collection from that folder, it gets to 92% then seems to finish, and just stays on 'please be patient while amarok scans your music'

I have tried sqlite and mysql databases.

---

### Post by peteresch on 2006-06-12
I also mount a samba share for my music.  When amarok is first building the collection it seems to hang.  I re-ran the First Run wizard and then restarted the app.  It was then able to build the collection.  It took about 5 minutes for 2200 songs.

---

### Post by Cyfr on 2006-06-14
I found a solution to my problem, i added 

file_mode=0444,dir_mode=0555 on to the end of my mount line in fstab. It then worked correctly

---

### Post by goldenboy on 2006-06-27
[QUOTE=Cyfr]...
file_mode=0444,dir_mode=0555 on to the end of my mount line in fstab. It then worked correctly[/QUOTE]

Hi, I'm having the same problem, but in my case amarok stops working after 20% - I have to admit that I'm having a really huge collection... - and after that I'm not able to access the mounted samba shares on the machine anymore, even after terminating amarok... Before switching to (K)Ubuntu 6.06 everthing worked quite well.

The PostgreSQL database is runnig on the same machine as the samba server,  if this is of any interest.

Do the above options work for smbfs, too? I'm using the fmask and dmask options, but perhaps I should give yours a try?!

Cheers, Daniel.

---

