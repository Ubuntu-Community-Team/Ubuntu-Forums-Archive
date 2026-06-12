---
title: "Some beagle troubles"
date: 2006-06-12
forum: Desktop Environments
---

### Post by rtrujillo on 2006-06-12
Hi, 

sorry if this post goes not here. I don't know where exactly to place it.

I instaled Dapper ( stable ) on my notebook, with beagle and deskbar. Beagle works fine, but for some reason i can't understand, after some days, beagle stops to work. 
I google it, and search on this forum a solution but can't find anyone so i format the hard disk and re-installed ubuntu again ( with all updates and beagle. ) And again i found with the same trouble: it works fine for the firsts days but after these days it stops to work.

Another corious thing is: I change the directory to index to my home directory so it should index only my home and its subdirectories. If i search deb on beagle i get a result on /usr/share/...etc ( out from my home!! ). If i try  after reboot, i get hte same. I i create a new text file on desktop with word hello i cant' find it.

Anyone can help me?

Thanks.

---

### Post by rtrujillo on 2006-06-12
anyone can help me?

---

### Post by rtrujillo on 2006-06-13
noone?

---

### Post by colgate on 2006-07-03
Hi
i get almost the same problem!
when i start beagle forcing indexing (export exercise_the_dog=1 or similar) everything is fine.
But when i start it normally it doesn't index my files! I can still search between files already indexed.... (i've never experienced results with file outside my home dir) 
But more weired is that STILL index my IM log! It just doesn't index my files.
I have extended attributes on.

Anyone know the cause?


Federico

---

### Post by porchcth on 2006-07-03
Dear rtruchillo,

I had the problem once (beagle suddenly stopped working). My solution was to delete the .beagle folder in my home directory.
After that, it indexed and worked again.

Regards,

porch.

---

### Post by cptnapalm on 2006-07-04
What does running beagle-search from the command line say?

---

### Post by anil_robo on 2006-07-09
I have two issues to speak of:

1. Beagle **does** index my files in the home directory, but not instantly. Usually, I must leave the computer idle for 10-20 mins before I can see the file indexed.

2. It indexes my home directory, but not its subdirectories. This is so inconvenient, I don't want files lying around in the home directory, so I arrange them neatly in folders. Since the files are in the subdirectories rather than the home folder itself, they are not indexed! Is there a way to circumvent this?

---

### Post by cicoandcico on 2006-07-16
i have the same problem. the only solution is removing the .beagle folder from my home directory. what a mess!

---

### Post by colgate on 2006-07-17
I've already did that!
same problem after reboot....

Federico

---

### Post by mthaddon on 2006-07-21
Same thing here. Not indexing any documents. Deleted .beagle directory. Had to then restart the beagle daemon. Searched for the contents of a file that's in my home directory (text file).

Nothing.

---

### Post by Saul Howard on 2006-07-23
Same problem for me Beagle indexed some files when first installed with Dapper and nothing since.

should I delete the .beagle directory then?

---

### Post by dannemil on 2006-07-23
I gave up on beagle - too buggy for me. I've been reasonably happy with this java desktop index/search.

[http://java.com/en/desktop/autofocus.jsp]("http://java.com/en/desktop/autofocus.jsp")

Jim

---

### Post by mustekala on 2006-08-02
Same for me. I have Beagle on Dapper; I have scoured the net for answers but none so far. It just doesn't index other partitions.

---

