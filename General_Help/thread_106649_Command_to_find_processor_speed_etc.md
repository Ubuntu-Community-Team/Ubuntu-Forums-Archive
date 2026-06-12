---
title: "Command to find processor speed etc ?"
date: 2005-12-21
forum: General Help
---

### Post by petef on 2005-12-21
Hiya,

Im very new to linux\unix and thought I would give it a go, the system is up and running although is fairly slow compared to windows xp ?

Im unsure of the processor I am using in the system i have it installed on I know I could take it apart and find out by having a look inside but is their an easy way to find out things like the processor speed, ram etc ?

Cheers

Pete

---

### Post by void_false on 2005-12-21
$ cat /proc/cpuinfo

---

### Post by mcduck on 2005-12-21
'cat /proc/cpuinfo' will give you processor speed and other CPU-related stuff.

'top' will give you info about memory and cpu use of running programs. press 'q' to quit top.

---

### Post by petef on 2005-12-21
Thanks for the info guys. My machine's a celeron 1.4 with 128meg of ram i only seem to have 2.5meg free of ram ? Would you expect Ubuntu to be running OK on this system ?

Cheers

Pete

---

### Post by drogoh on 2005-12-21
Linux can run fine on old hardware and/or low resources, just watch what you run.  I wouldn't expect full-blown Gnome or KDE to run all that great.  Personally, I would look into a little more memory.  If you can spring for it, go for 512M.  Your computer and your Ubuntu install will thank you.

---

### Post by petef on 2005-12-21
Thanks. Will try increasing the RAM :)

Pete

---

### Post by void_false on 2005-12-21
You can get more info on specified subject by looking at files inside /proc directory
Use:
`ls /proc` to get list of files
and then
`cat /proc/<name-of-file>` to get the actual information.

---

### Post by petef on 2005-12-21
Cheers dude. Giving that a try now :)

Pete

---

### Post by s26c.sayan on 2007-02-25
Same question for me.....and the solution works for me!! :)
Thanx mates!!! :)

---

### Post by Mujaheiden on 2007-04-12
thank for me too. Only the top command doesnt say very clearly what is the memory, but i assume 

Mem:    904552k total,   891888k used,    12664k free,    44808k buffers
Swap:  2650684k total,        0k used,  2650684k free,   543460k cached

means I have 1Gig.

---

### Post by Hallvor on 2007-04-12
petef: With specs like that, I would add another 256 mb of ram or run Xubuntu. Regular Ubuntu will feel a bit sluggish on a computer like yours with that little ram.

---

