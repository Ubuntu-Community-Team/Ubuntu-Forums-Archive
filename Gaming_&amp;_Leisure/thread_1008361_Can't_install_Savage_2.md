---
title: "Can't install Savage 2"
date: 2008-12-11
forum: Gaming &amp; Leisure
---

### Post by daariil on 2008-12-11
Hello. Sorry for being a total newb but the Savage 2 install just wont start.
When i click it Gedit opens but freezes.
And when i try to run it in the terminal i use this command:

$ cd /home/joel/Skrivbord
~/Skrivbord$ chmod +x Savage2Install-1.5.0-x86_4.bin

But then what?
What should i do next?

/Joel

---

### Post by Perfect Storm on 2008-12-11
[http://gaming.gwos.org/doku.php/guides:64bit:savage_2](http://gaming.gwos.org/doku.php/guides:64bit:savage_2)

---

### Post by daariil on 2008-12-11
yes i did follow that but when i type that last line it said something like it couldn't start it becaus it's a bin file

---

### Post by Perfect Storm on 2008-12-11
Try

```
sh Savage2Install-1.3.99-x86_64.bin
```

---

### Post by daariil on 2008-12-11
then i get this: 

Savage2Install-1.5.0-x86_4.bin: 1: Syntax error: word unexpected (expecting 
")")

what does it mean?

---

### Post by Perfect Storm on 2008-12-11
Can I get the exact output when you do ./Savage2Install-1.5.0-x86_4.bin (forgot to ask about it).

---

### Post by Grishka on 2008-12-11
check the file properties. it must be set as an executable.

---

### Post by daariil on 2008-12-11
well it's in swedish

bash: ./Savage2Install-1.5.0-x86_4.bin: det går inte att köra binär fil


"det går inte att köra binär fil" means that it cant run a .bin file

---

### Post by Perfect Storm on 2008-12-11
Tried Grishkas suggestion?

---

### Post by daariil on 2008-12-11
it is set as executable

---

### Post by Grishka on 2008-12-11
if nothing helps, perhaps your download got corrupted somehow. you might consider redownloading the file. use the bittorrent link from the official page, this will ensure that your download doesn't get corrupted.

---

### Post by Vadi on 2008-12-11
Your download is corrupted - please redownload.

---

### Post by daariil on 2008-12-12
Im going to try that thanks :)

---

### Post by daariil on 2008-12-12
this torrent is NOT going very fast :P
i download 1-5 kB/s :(

---

### Post by Vadi on 2008-12-12
Use http

---

### Post by Grishka on 2008-12-12
> **daariil said:**
> this torrent is NOT going very fast :P
i download 1-5 kB/s :(

you isp may be blocking some ports. try enabling encryption in your bittorrent client. or maybe you're behind some restrictive router.

---

### Post by daariil on 2008-12-12
no i dont think it's anything like that because i can download other torrents just fine with like 1,3 Mb/s so maby its just the tracker that is bad now.

---

### Post by daariil on 2008-12-13
okey now i have tried every single one of those downloads from their webpage and i get the same error with all of them.

so now i have absolutely no idea what to do :S

---

### Post by Vadi on 2008-12-13
Post on their support forum: [http://forums.savage2.com/forumdisplay.php?f=8](http://forums.savage2.com/forumdisplay.php?f=8)

---

### Post by Grishka on 2008-12-13
> **daariil said:**
> okey now i have tried every single one of those downloads from their webpage and i get the same error with all of them.

so now i have absolutely no idea what to do :S

idk, man. I've downloaded s2 via torrent, and it works for me. either you're missing something, or there's something seriously screwed up with your system. all I had to do was: download, set file to executable, and execute to install.
another thought: maybe you're trying to run a 64-bit executable on a 32-bit system?

---

### Post by Vadi on 2008-12-13
Yeah, that turned out to be the issue

---

### Post by thelastunavail on 2009-04-11
> **Grishka said:**
> check the file properties. it must be set as an executable.

Thank you! You are the man.

Worked perfect, i will have to remember this for the future.

---

