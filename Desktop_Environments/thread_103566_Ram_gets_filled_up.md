---
title: "Ram gets filled up"
date: 2005-12-14
forum: Desktop Environments
---

### Post by jan-banan on 2005-12-14
i used linux for a whole day once som days ago, and when i shut it down i only had about 100Mb RAM free (out of 512) and some of my swap was filled to, but the thing is that when i shut i down, i was only running gaim, amarok and gdesklets (and that is where i got my RAM-checker)

when i freshly boot my computer, i have about 350 Mb free.
i asked some guys on IRC and they said that it might be some sort of cache-thing going on? i dont like it, i like my computer fresh in all ways, and i allready compomised with linux since i kind of HAVE to have all programs that follows for it to work well (and by well, i mean like my win XP wich is 150Mb installed... i used nlite in case you wondered)

what can i do? is there something i can shut off to make this go away?

in brief, my computer filosofie is LIGHT and easy, the closest i have come is ubuntu which fixes everything from the start but unfortunately is about 2gb installed and uses lots of RAM after a while:(

---

### Post by DrBair on 2005-12-14
Check /proc/meminfo for more information on memory usage. You are concerned about memory that is ACTIVE.  Active memory is just that, being used by a running program.  If that value is getting very high you can check memory usage of different programs using the command 'top'.  Somethings leak memory because they are evil, so look for things consuming excessive amounts of memory.  


Also, free memory is essentially WASTED memory. Almost all memory should be used for something except for right after startup. After that point the OS should start caching and buffering stuff for future use, it can then throw that stuff out as needed to make room for more apps to be loaded.

---

### Post by jan-banan on 2005-12-14
ok...
so windoz, is it just really inefficient or what? is a (good) OS supposed to practically fill the RAM as soon as possible to ensure a faster computer?

in that case, how dows it work when a big RAM-eater gets started when the RAM is filled with cahce for other programs? say that you are running gaim, firefox, amarok and have done so all day resluting in your RAM being filled almost to the max, and then you start "program X" that uses tons of RAM, what happens? will it flush all cached memory and put "program X" there instead, resluting in a kind of rebooted computer when you shut "program X" off again? in that case, all i need to do when my RAM gets filled with cache is to start a huge needy program that flushes my system when i shut it off making my problem go away :D

---

### Post by GeneralZod on 2005-12-14
[QUOTE=jan-banan]ok...
so windoz, is it just really inefficient or what? is a (good) OS supposed to practically fill the RAM as soon as possible to ensure a faster computer?
[/QUOTE]

Absolutely.  RAM access is orders of magnitude faster than disk access, so often-used files should be cached in RAM as much as possible.  Windows takes this to excess, somewhat - it will sometimes page apps out of memory and into swap when there is absolutely no need to do so, which can lead to swappiness when switching back to an app you used a while ago.

> 
in that case, how dows it work when a big RAM-eater gets started when the RAM is filled with cahce for other programs? say that you are running gaim, firefox, amarok and have done so all day resluting in your RAM being filled almost to the max, and then you start "program X" that uses tons of RAM, what happens? will it flush all cached memory and put "program X" there instead, resluting in a kind of rebooted computer when you shut "program X" off again?


I'm no expert, but this seems roughly right :)

> 
 in that case, all i need to do when my RAM gets filled with cache is to start a huge needy program that flushes my system when i shut it off making my problem go away :D

It's only a problem if you make it one :D Seriously, using up all RAM is a *good* thing and should lead only to increased performance.

---

### Post by tlc on 2005-12-14
What GeneralZod said. :p 

Linux manages memory a bit differently than windows, that's all, and is widely viewed as being better at it.

---

