---
title: "Problems with MP3s and Video playback"
date: 2006-09-11
forum: Desktop Environments
---

### Post by bertcakes on 2006-09-11
Ok, first off. I do have XGL/Compiz installed. It appears these may cause some issues. 


I can NOT get xmms to play ANYTHING. I have read everything off the of restricted formats page and nothign will work. I have installed everything possible that I can think of and it will do nothing with I try to play an MP3. It just sits there and looks at me cross eyed. Now, MP3s DO work w/ Totem...but I cant stand Totem.


Second, I can NOT get mplayer to work for the life of me. Once again, Totem seems to play everything fine (except its damn buffering when playing divx/xvid files). But I can not get Mplayer to play anything. It does absolutely NOTHING. I have also read and tried everything off of the resitricted formats section. I even installed some codecs using Automatix...no luck. I have run out of options. Is it XGL...or does it have nothing to do with that. 

Any help would be GREATLY appreaciated. Basically, things work...just not right. Xmms plays NOTHING and Mplayer...plays NOTHING. Totem works...but plays avi files like crap...if you try to skip forward it takes like 15 minutes to buffer...

Please help

n00by mc-n00b

---

### Post by bertcakes on 2006-09-11
Any ideas? 


Xine wont play crap either...its really starting to annoy me...this is one of the reasons I dont fully switch to linux...things that just work in windows...dont in linux. 

Please, any ideas?

---

### Post by bertcakes on 2006-09-11
VLC...nothing...it doesnt do a damn thing when I try to play something with it...any ideas?

---

### Post by bertcakes on 2006-09-11
Ok, so i think i figured it out and i feel like a moron for it...im not 100% how to fix it, but its not a codec issue. Basically, I have a PC that has all my media files on it (not the linux box) and when I goto network servers and access it...it will not play ANY audio or video files unless i use totem...however, if i copy and paste that to my home directory i can play those files with mplayer for video and xmms for mp3s...so im assuming its some sort of file sharing issue...i dunno.

---

### Post by bertcakes on 2006-09-11
Does anyone know how to fix this?

---

### Post by bertcakes on 2006-09-12
Ok, let me explain a bit more.

I am just so so when it comes to linux. I can get myself by and when I dont know something, I will spend hours to fix it (just like this). What started out as a possible codec issue turned out to be nothing of the sort. 

I have a windows XP box that has about 500 gigs worth of various media, the drives are NTFS. All I did in my Bunutu box was goto Places -> Network Servers -> and from there I browsed to my own network and was able to see and share my files. I have the ability to delete files and rename on those NTFS drives from my linux box. What does NOT work...is mplayer or xmms or any other media player other than totem...now I wouldnt mind totem if it didnt have such a hard time buffering my AVI files. If i try to fast forward any of my AVI files it takes like 15 minutes to buffer them. If I try to (for example) open an MP3 with xmms...it doest play, it doesnt register that anything was requested to play through it. Even though I set it to the default MP3 player...but if I open it in totem it does...now lets take an AVI...if I try to open it with Mplayer (which is the default video player) it does the exact same thing, it doesnt register that it has a file to play. However, in both cases, if I copy that file to my ubuntu box and play it locally....it works flawlessly...PLEASE are there any ideas? I really cant find any info on this. 

One more note, it doesnt matter if I do this as root, or as me. 

I have now verified this problem on two different linux boxes trying to access two different windows machines.

---

### Post by Scorpuk on 2006-09-12
Have you tried mounting your windows drive?


You can find out how to do this [here]("http://www.ubuntuforums.org/showthread.php?t=236564").

---

### Post by bertcakes on 2006-09-12
Maybe this is just me...but why do I have to do that? It doesnt make sense to me to mount it that way if it works perfectly fine the other way (other than the effing media). 

This is one of the little things that leaves people from leaving windows to linux. 

Additionally, when I tried what was suggested in that post...it didint work. :(

I'm just getting flustered with this tiny problem.

---

### Post by TransitMan on 2006-09-12
You need to recheck your permissions in the Windows portion of your computer.
Then recheck your permissions in Linux, and make sure the mounts are correct. Just because you can delete and rename files from Linuix to NTFS isn't the same as playing them.
I had to fiddle with permission issues on my NTFS partitions when I first got into Linux, but now, with the eprmissions taken care I have nary a problem.

Also, getting flustered over this tiny problem makes you learn more as well. This is how I have learned, both from my Window days into my beginning Linux days.

---

