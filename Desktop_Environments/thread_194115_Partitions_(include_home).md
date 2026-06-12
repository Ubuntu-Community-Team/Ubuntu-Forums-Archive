---
title: "Partitions (include /home)"
date: 2006-06-11
forum: Desktop Environments
---

### Post by ESPOiG on 2006-06-11
i that is it, what i want to do is partition my hdd into sections so when next i goto install ubuntu i can keep my /home directory ??... if that makes sense

so it would look like this or something

swap - 1.5gb
/ - 50gb
/home - (remaining space)

is that right and does anyone know what i mean :P... plz help me

ty, ESPOiG

---

### Post by uzi09 on 2006-06-11
[http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html)

---

### Post by user1397 on 2006-06-11
yes read the guide that uzi09 suggested.

depending on hard drive size, your partitions will be different.  i have a 150 GB hard drive and 1 GB of ram, so i made my partitions like this:  15GB for **/** , 134GB for /home , and 1 GB for swap

i actually backed up all of my files into one folder called "ubuntu", into my windows pc's shared folder, using my home network, then i installed dapper fresh as anything, then just imported the "ubuntu" folder back to my new dapper pc.  while installing it, i made the aforementioned partitions :p

---

### Post by ESPOiG on 2006-06-11
k so i can do it, but i am also wondering - (edited) this is gunna be a fresh install, just so u know :D

eg. 

swap - 1gb
/ - 19gb - ext3
/home - 40gb - ext3

i have only ever used the auto config, so ext3 for / and /home swap is swap and then do i make them logical, primary or something and which do i boot from, it is / aint it??

i just wanna know all this before i get somewhere i dont know and stuff it up :D

:S ty, ESPOiG

---

### Post by user1397 on 2006-06-11
[quote=ESPOiG]k so i can do it, but i am also wondering - (edited) this is gunna be a fresh install, just so u know :D

eg. 

swap - 1gb
/ - 19gb - ext3
/home - 40gb - ext3

i have only ever used the auto config, so ext3 for / and /home swap is swap and then do i make them logical, primary or something and which do i boot from, it is / aint it??

i just wanna know all this before i get somewhere i dont know and stuff it up :D

:S ty, ESPOiG[/quote]
i wouldn't make your / partition so big, 15 GB is more than enough (and yes that is the one you boot from)

i particularly don't think much about primary and logical, it's never made a difference in my partitions, so do w/e you want for that stuff.

and yes / and /home are ext3 while swap is just swap

---

### Post by bulldog on 2006-06-12
If you have an empty HD you shouldn't be worried about primary and logical, if you make only this three partitions that is.
Create a swap, a '/' and a /Home ,format and install.:) 
That's it.

---

