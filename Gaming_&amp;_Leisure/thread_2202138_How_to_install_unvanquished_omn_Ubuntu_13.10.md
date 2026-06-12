---
title: "How to install unvanquished omn Ubuntu 13.10?"
date: 2014-01-27
forum: Gaming &amp; Leisure
---

### Post by alex2356 on 2014-01-27
I have been trying to install the game `unvanquished` on Ubuntu 13.10 without success. I tried to install this game by downloading the file `unvanquished-common_0.23.0-2~ubuntu.13.10_amd64.deb` (I cannot tell which webpage anymore). After that, I was installing this package with `sudo dpkg -i`. After half an hour, downloading a lot of stuff, it said 'Finished'. However, when starting the game I got an error: 

```
./unvanquished: error while loading shared libraries: libSDL2-2.0.so.0: cannot open shared object file: No such file or directory
```

Do I miss something? Did I miss some strange package again? Should I start all over again with some other approach? Is there an EASY way to fix this?

Here some more information on my computer:

CPU: Intel(R) Pentium(R) CPU 2020M @ 2.40GHz
MemTotal:        3924776 kB
Linux LenovoG700 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Let me know if you need more information (and how to get it).

P.S. Do people know of similar free games (first/third person shooter) that will work on this computer system, is easy to install, will have decent graphics, works in multiplayer online mode, has a fullscreen option, and can be EASILY installed (e.g. by using apt-get install?)? I know, I am requesting something almost impossible, but maybe I have luck and there is a FREE game satisfying all my requirements...

---

### Post by oldrocker99 on 2014-01-28
Alien Arena, Blood Frontier, Sauerbraten, Warsow, Xonotic are all multiplayer first-person shooters in the Ubuntu repositories, and will install all needed dependencies along with the games. I know that there are more, but those are listed off the top of my head. If there is one game genre well-represented for Linux, it's FPS.

You probably downloaded it from SourceForge, BTW.

You can also try:

sudo apt-get install libsdl

and see what happens. Good luck!

---

