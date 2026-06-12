---
title: "I hate you WoW, But I need you"
date: 2007-08-26
forum: Gaming &amp; Leisure
---

### Post by downgrade on 2007-08-26
Ok this is weird. I posted friday or early saturday about my WoW install dying and not letting me install again. Well after reinstalling 7.04 completely and it working flawlessly, it stopped working the exact same way.
One of the MPQ compressed files, a small part of it dies, which didn't allow me to play 2 characters, but I figured, this time things will be differnt, I will reinstall and nothing will be bad... well I was wrong, the files I installed from not even 24 hours were also corrupted (another MPQ)

Soooo, I am going to finish downloading the installer you can get online, if that fails I will try different RAM (considering it took me several times to reinstall Ubuntu because it kept freezing when partitioning the drive), and if that fails I will cry for a bit because the RAM was expensive and I probably don't have any warranty paperwork or something, I dont know, Then I will fight with reinstalling Ubuntu, setting up everything perfect, backing it up, and just assuming I will have to recover off that every few days for some reason... but I am guessing its a hardware problem because this happened in windows too, but I did badblocks twice and both times there were no errors... 

any ideas? RAM? Drive that just passes badblocks but is actually bad?

UPDATE: 
Took out my dual channel RAM kit, put in an old gig stick that hasn't been used since I started using this new RAM. Same thing, so either that RAM is also crapped (doubt it) or Ubuntu or wine hates files name "common.mpq" it seems like.

If you go down a few posts you will see my crappy "log" of errors on this post
[http://ubuntuforums.org/showthread.php?t=534205]("http://ubuntuforums.org/showthread.php?t=534205")
Im still working on it, the downloader is still working away too, 14%. any ideas?

although I am getting a differnt set of errors now, saying maybe there is a problem with my Z device, but I havent changed it in wine, I dont know. I am gonna try recopying the install files over and over until the installer is done.

---

### Post by orionsbelt on 2007-08-30
How are you installing WoW?  You actually need to install it through the wine command.

Wonderful documentation can be found here:  [https://help.ubuntu.com/community/WorldofWarcraft#head-ffdb6e1abf69e93f2ee1bad73a59c4fc17a295db](https://help.ubuntu.com/community/WorldofWarcraft#head-ffdb6e1abf69e93f2ee1bad73a59c4fc17a295db)

This also includes instructions for downloading from Blizzard's site, including which ports need to be open.

---

### Post by derekr44 on 2007-08-30
I'll continue to give free advertising (lol)

Try the Crossover demo.  Worked flawlessly for me.

I did notice that the WoW news splash screen does attempt to download a 16kb file and just sits there.  So I do 2 things...

1. Manually download any patches from Fileplanet and apply them directly via Crossover
2. Run WoW.exe directly from my Crossover install rather than the launcher.

---

