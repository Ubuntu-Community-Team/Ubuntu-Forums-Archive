---
title: "Quake2 Mission Pack Problems"
date: 2006-03-13
forum: Gaming &amp; Leisure
---

### Post by AndyAWS on 2006-03-13
Has anyone managed to get the "The Reckoning" and/or "Ground Zero" Mission packs to work. I have installed the pak files and I can get them to load, however no new enemies or weapons will work. I get an error about not being able to spawn the gekks in level one of The Reckoning.

I have tried with both the loki installer and with the quake2 deb pack from the repos.

All I have been able to find out by digging for info is that I need the gamei386.so files for each of the mission packs, however I haven't had any luck finding them or compiling them myself from ID source. Any that I've tried give me an "deploying SDL pararchute" error when I try to stat a new game.

If anyone has working game.so or gamei386.so files, or any other ideas, I'd really appreciate a little help.

Thanks.

---

### Post by AndyAWS on 2006-03-14
Ok, I tried compiling the source code from the repo last night, with the mission pack source code from ID's ftp. During the configure it announced that it found the xatrix and rogue sources. I was unable to tell if did anything with them during the make, however there were no game.so files created under the xatrix and rogue folders after running make. Make install crashed immediately with file not found.

Does anyone have the Quake2 mission packs working on their system, and how exactly did you do it?

---

### Post by vasdee on 2006-03-28
copy the mission pack directory (rogue, xatrix, etc) to /usr/share/games/quake2 then cd to that directory and run via

```
quake2  +set game xatrix
```

---

### Post by AndyAWS on 2006-03-28
Yes, I know how it is supposed to work, and it will run and load the proper maps and even play the video, however you will not have any of the new weapons and the new enemies will not be spawned, because you need the proper [COLOR="Red"]game.so [/COLOR]library file for each add-on. Try running xatrix, then pull down the console and put in **give all**, then flip through your weapons, the new ones are missing. Wander around and try to find any grekks (amphibian creatures that throw acid).

The quake2 in the repos was not compiled with support for the mission packs, as far as I can tell. If it was, there would already be xatrix and rougue folders with a game.so file in each. Likewise for the Loki installer version.

---

### Post by vasdee on 2006-03-28
ahh ok. I was wondering why the first xatrix map was so empty :) 

Maybe there is a custom deb package somewhere? Could you link here if you find one? cheers!

---

### Post by AndyAWS on 2006-03-29
[URL="http://www.markshan.com/thesinraven/linux_quake_2_q2max_v.3.21_r0.15.htm"]http://www.markshan.com/thesinraven/linux_quake_2_q2max_v.3.21_r0.15.htm
[/URL]

Not Deb packages, but easy to install. Has support for the Mission Packs including the 3rd and little known Zaero Mission Pack, and has Erasor Bot support available to download.

Remove the repo Quake2 packages first. 

Follow the install instructions in the Read-Me.

Works great so far, Xatrix is a lot harder when all of the enemies are spawned properly. Also you can now get past the "need green key card" level, since the green key card actually exists now.

---

### Post by AndyAWS on 2006-03-30
Scratch the above, it still doesn't completely work. The Reckoning Mission Pack (xatrix) refuses to continue after getting on the train which completes the first segment. It just sits at the camera shot, I can pull down the console, and enter the menu, but the next map refuses to load, no errors.

Here is the solution, at least for me, for now....

Download and install the Quake2 loki installer for 3.21r16 from here : [http://www.liflg.org/?catid=6&gameid=55]("http://www.liflg.org/?catid=6&gameid=55")

Download the quake2 binaries for 3.21r15 here: [http://www.markshan.com/thesinraven/linux_quake_2_q2max_v.3.21_r0.15.htm]("http://www.markshan.com/thesinraven/linux_quake_2_q2max_v.3.21_r0.15.htm")

From sinraven's r15 archive, extract the xatrix and rogue folders and copy them into the loki r16 install at /usr/local/games/quake2/

Now insert your pak files (and video folders) into the proper game folders under /usr/local/games/quake2/ (base - xatrix - rogue)

You can also try to get Zaero working by extracting the zaero folder from sinraven's archive and finding the zaero demo on the web to get the pak file, good luck, crashes for me with an error about a tank materializing in a solid.

But The Reckoning and Ground Zero will work fine.

---

### Post by vasdee on 2006-03-30
thanks heaps for this! much appreciated :)

---

