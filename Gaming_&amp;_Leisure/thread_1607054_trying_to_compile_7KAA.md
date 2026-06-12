---
title: "trying to compile 7K:AA"
date: 2010-10-27
forum: Gaming &amp; Leisure
---

### Post by ELD on 2010-10-27
Hi everyone trying to compile 7K:AA -> [http://7kfans.com/](http://7kfans.com/)

Got an error that stops me though:
> 
liam@liam-desktop:~/Downloads/7kaa$ perl configure.pl
Platform: linux32
Detecting gcc version: 4.4.5 ok
Checking for SDL: found
Checking for OpenAL: found

Ready to run build.pl

liam@liam-desktop:~/Downloads/7kaa$ perl build.pl
Entering 'src'.
Entering 'audio/openal'.
g++ -c -g -DAMPLUS -DUSE_OPENAL -DUSE_SDL -DDEBUG -DNO_ASM -DNO_WINDOWS -I../../../include openal_audio.cpp -o openal_audio.o
build.pl: couldn't build 'cpp'. Stopping.


---

### Post by Perfect Storm on 2010-10-27
Does it contain a log file in its directory?

---

### Post by ELD on 2010-10-27
None that i can see :(

---

### Post by Perfect Storm on 2010-10-27
Then it's going to be hard to track down the problem. I think it would be best to contact the 7K crew.

---

