---
title: "Quake 2 Help"
date: 2006-07-15
forum: Gaming &amp; Leisure
---

### Post by andy- on 2006-07-15
This is probably a simple problem, but I'm just too new to know the answer.

I'm trying to install Quake 2, and Rocket Arena 2. I downloaded Loki installers for both. Went to terminal and gave it a try, came back with this result:

[LIST]
[*]andy@home:~/Desktop/Quake$ sudo sh quake2_3.21-r0.16.1-english.run
[*]Verifying archive integrity... All good.
[*]Uncompressing Quake II 3.21+r0.16.1 Installer.....................................................................
[*]/home/andy/.setup26883: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
[*]andy@home:~/Desktop/Quake$
[/LIST]

Ok, spent half hour looking for the right libgtk-1.2.so.0 and found it. First tried to extract just the libgtk-1.2.so.0 by itself to /usr/lib/ same result. Then extracted the two folders that came with downloaded GTK pack /etc/gtk/ and /usr/lib/ and /usr/share/ ...
Still getting same error. Any input would be highly appreciated.

Thanks in advance. :) 

p.s. If anyone has a good walk-through link, so I can just follow the instructions there, would be nice. I've googled for a couple days and read the forums, nothing that really explains Loki installers.

---

### Post by DoktorSeven on 2006-07-15
Tried just installing libgtk1.2 from Synaptic or apt-get?

**sudo apt-get install libgtk1.2**

---

### Post by andy- on 2006-07-15
hmm, after 2 days of doing this, I must have went braindead. That fixed the problem lol thx alott :)

---

### Post by andy- on 2006-07-15
Quake 2 installed. Runs fine etc.

Any idea what to do about this:

[IMG]http://img68.imageshack.us/img68/8955/screenshotcn4.png[/IMG]

Rocket Arena 2 Doesn't see the game. I also tried running it from /usr/local/games/quake2/ get the same message.

---

