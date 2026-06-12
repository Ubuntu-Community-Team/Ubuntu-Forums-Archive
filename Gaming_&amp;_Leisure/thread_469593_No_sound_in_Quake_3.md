---
title: "No sound in Quake 3?"
date: 2007-06-10
forum: Gaming &amp; Leisure
---

### Post by thegreenblob on 2007-06-10
I just installed quake 3 and I am not getting any sound?

Any ideas?

I am running ubuntu feisty 32 bit.

I got this in the terminal for sound initialization.

------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------

---

### Post by Sockerdrickan on 2007-06-10
sudo apt-get install libopenal0a

Close programs that uses sound.

---

### Post by Nehvrook on 2007-06-10
Go to wherever you installed Quake III (For me this was /home/lee/ProgramFiles/Quake3) and in that folder find the baseq3 folder. Inside there will be a bunch of archive files. Using the archive manager (comes with Ubuntu) open the one called pak0.pk3 (You'll have to change the permissions to let you read and write to this file) and find the music folder and hit delete. (I made a backup of pak0.pk3 (Just copy it somewhere else on your hard drive in a folder called backup or something) just in case)(This part is required because the music can cause the game to crash after you apply the fix below)

Once you've deleted the music folder close the archive manager and go to the root terminal. In the root terminal type in
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
and hit enter
Then point the terminal at your quake 3 file (For me this was /home/lee/ProgramFiles/Quake3/quake3) and it will launch the game with sound and it shouldn't crash when you load maps

Also see this link about making a launcher so you don't have to type this out each time
link [http://ubuntuforums.org/showthread.php?p=2646720#post2646720](http://ubuntuforums.org/showthread.php?p=2646720#post2646720)

There have been loads of people with this problem so a search for quake sound will bring up loads of threads solving the problem if you get stuck :)

---

### Post by thegreenblob on 2007-06-10
Man... when I tried to delete the folder I got an error. :(

It was:

	zip warning: local header not found for sound/player/bitterman/death2.wav

zip error: Zip file structure invalid (/usr/local/games/quake3/baseq3/pak0.pk3)


Any help here?

---

### Post by Nehvrook on 2007-06-10
Hmm that's strange. Never heard of anyone having that problem before.

Have you tried extracting the whole of pak0.pk3 into just ordinary folders, Deleting the music folder in Nautilus and recompiling the folders back into an archive called pack0.pk3. 

Replace the origional with the one you just made and that should work.

---

### Post by thegreenblob on 2007-06-10
Just tried it and got the same error :/

---

### Post by thegreenblob on 2007-06-10
Thanks man! Got it working.

I repaired the archive with winrar in wine. And I was able to delete the music folder. And its working now! Thanks!

---

### Post by Nehvrook on 2007-06-14
No problem, glad I could help :)

---

### Post by Divan Santana on 2007-08-22
> **Nehvrook said:**
> Go to wherever you installed Quake III (For me this was /home/lee/ProgramFiles/Quake3) and in that folder find the baseq3 folder. Inside there will be a bunch of archive files. Using the archive manager (comes with Ubuntu) open the one called pak0.pk3 (You'll have to change the permissions to let you read and write to this file) and find the music folder and hit delete. (I made a backup of pak0.pk3 (Just copy it somewhere else on your hard drive in a folder called backup or something) just in case)(This part is required because the music can cause the game to crash after you apply the fix below)

Once you've deleted the music folder close the archive manager and go to the root terminal. In the root terminal type in
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
and hit enter
Then point the terminal at your quake 3 file (For me this was /home/lee/ProgramFiles/Quake3/quake3) and it will launch the game with sound and it shouldn't crash when you load maps

Also see this link about making a launcher so you don't have to type this out each time
link [http://ubuntuforums.org/showthread.php?p=2646720#post2646720](http://ubuntuforums.org/showthread.php?p=2646720#post2646720)

There have been loads of people with this problem so a search for quake sound will bring up loads of threads solving the problem if you get stuck :)

This worked for me just as he said! :)

Thanks very much! Love ubuntuforums :)

---

