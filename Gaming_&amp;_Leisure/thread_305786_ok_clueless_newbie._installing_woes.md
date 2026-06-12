---
title: "ok clueless newbie. installing woes"
date: 2006-11-23
forum: Gaming &amp; Leisure
---

### Post by Redlance on 2006-11-23
tried to install sword of fargoal using this how to
"http://gaming.gwos.org/index.php?option=com_content&task=view&id=181&Itemid=63"

any way got compile errors 
gcc -W -Wall -O3 `allegro-config --cflags` -DLINUX    -c -o char.o char.c
/bin/sh: allegro-config: not found
In file included from char.h:4,
                 from char.c:1:
main.h:4:21: error: allegro.h: No such file or directory
In file included from char.h:4,
                 from char.c:1:
main.h:21: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
In file included from char.c:2:
map.h:63: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
map.h:64: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from game.h:3,
                 from char.c:3:
message.h:13: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SAMPLE&#8217;
message.h:13: error: format string argument not a string type
message.h:14: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;SAMPLE&#8217;
message.h:14: error: format string argument not a string type
In file included from char.c:3:
game.h:10: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:11: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:12: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:13: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:14: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:16: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:17: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:18: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:19: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:20: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:21: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:24: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:25: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:26: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:27: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:28: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:29: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:30: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:31: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:32: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
game.h:33: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
In file included from char.c:4:
gfx.h:35: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
gfx.h:36: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
gfx.h:38: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
gfx.h:39: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
gfx.h:40: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
char.c: In function &#8216;encounter&#8217;:
char.c:127: error: &#8216;attack&#8217; undeclared (first use in this function)
char.c:127: error: (Each undeclared identifier is reported only once
char.c:127: error: for each function it appears in.)
char.c:140: error: &#8216;fight&#8217; undeclared (first use in this function)
make: *** [char.o] Error 1
pat@pat-desktop:~/Desktop/fargoal/src$ cd .. && rm -f sword.exe
pat@pat-desktop:~/Desktop/fargoal$ chmod +x runSword.sh
chmod: cannot access `runSword.sh': No such file or directory
pat@pat-desktop:~/Desktop/fargoal$ cd .. && mkdir ~/.Games
mkdir: cannot create directory `/home/pat/.Games': File exists
pat@pat-desktop:~/Desktop$ mv fargoal ~/.Games
mv: cannot move `fargoal' to a subdirectory of itself, `/home/pat/.Games/fargoal'

obviously lots of crap wrong here. my real question is... is there an idiot proof way to install things? (tried synaptic no joy sword isn't in there)
is there a repository i can add to make my life easier?

---

### Post by deepwave on 2006-11-23
Nothing is idiot proof.  People trying to make idiot-proof programs set themselves up for failure.  There is much to be said about user friendliness in programs though.

Anyways... in relation to your question.  I don't know of a repository for said game.  But I see that you are having problems compiling it.

gcc -W -Wall -O3 `allegro-config --cflags` -DLINUX -c -o char.o char.c
/bin/sh: allegro-config: not found

You need the allegro libs for your game, and the development files.  I believe these are covered in the allegro and allegro-dev pacakges.

When compiling, I find it useful to look at what ./configure spits out.  If it is looking for some library and fails, you will need to install the lib and its dev files to continue with the compilation.

Hope that helps.

---

### Post by Perfect Storm on 2006-11-24
It's me that wrote the howto. It looks like you missed some steps of the howto.
By the way it was tested on edgy so if you're running dapper I can't say for sure.


As deepwave said please post every step and output, it will make it easier to spot what went wrong (or I can spot an error in the howto).

---

