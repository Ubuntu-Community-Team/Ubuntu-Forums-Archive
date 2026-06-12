---
title: "how to port a win32 game to linux?"
date: 2009-06-09
forum: Gaming &amp; Leisure
---

### Post by bluesonic1 on 2009-06-09
Hi ~ 
Does anyone know how to port a game to linux? are there somekind of guides or programs? 
well .. ya ya ya..i know that reverse reverse engineering exists lol
but some help would be grateful

---

### Post by eldragon on 2009-06-09
> **bluesonic1 said:**
> Hi ~ 
Does anyone know how to port a game to linux? are there somekind of guides or programs? 
well .. ya ya ya..i know that reverse reverse engineering exists lol
but some help would be grateful

your question is vague, check the wine project.

---

### Post by Bölvaður on 2009-06-09
it's pretty simple if it is a simple game.

Just compile the source and see what bugs you get (it is better in my opinion than starting to try to find common differences)

a common difference in c++ and other is using

#include <sys/time.h>
instead of 
#include <time.h>

in linux you get the time like this for an instance
gettimeofday(&myVariable, NULL);
myVariable.tv_sec

not sure how it is in windows

---

### Post by benj1 on 2009-06-09
do you have the source to this game?

or is just a game that you would like to play on linux?

---

### Post by bluesonic1 on 2009-06-09
thanks for the replies
no i don't have the source code plus the file/files are packed 
it's not a game that i try to play for my own in linux lol
I'm trying to do it for the bomberman online community 
dont know if u heard of it .. the main site is [http://bmoworld.com](http://bmoworld.com) 
(hope i dont get warned for the site)
we haven't done really a progress..

[quote="WasserDragoon"][FONT=verdana][SIZE=1]I didn't big stuff yet. 
 
There are some little things: 
 
**Porting work** 
[[/SIZE][/FONT][FONT=verdana][SIZE=1][URL="http://dsource.org/projects/dwt-addons/browser/dwtx/novocode"]]]("http://dsource.org/projects/dwt-addons/browser/dwtx/novocode")[/SIZE][/FONT][FONT=verdana][SIZE=1][Ported Novocode's InternalShell Widget (Java) to D]("http://dsource.org/projects/dwt-addons/browser/dwtx/novocode")[/SIZE][/FONT][FONT=verdana][SIZE=1] 
 
**Other** 
[Created a class for easy usage of http post/file upload]("http://dsource.org/projects/tango.scrapple/browser/trunk/tango/scrapple/net/http/HttpMultipart.d")
[/SIZE][/FONT][/quote][FONT=verdana][SIZE=1]

game launcher porting..
[/SIZE][/FONT][quote="WasserDragoon"][FONT=verdana][SIZE=1][/SIZE][/FONT][FONT=verdana][SIZE=1]I started to port launch.exe
[IMG]http://www.img-teufel.de/uploads/Bildschirmfoto8910acd2png.png[/IMG]
You can download current files here: [http://www.file-upload.eu/download-1647062/bmo.tar.gz.html](http://www.file-upload.eu/download-1647062/bmo.tar.gz.html)
Who's interested in helping to port please post reply... [/quote]

p.s. source codes of the game wont be posted, cause we dont have it .. even the main admin doesn't have the game source code 
its a closed game that was re-opened..ermm..long story (check wikipedia for more)
[/SIZE][/FONT]

---

### Post by Vadi on 2009-06-09
Seems they're rewriting it with Mono. So it's not a port, its coding from scratch.

Port = take game source, adjust it to work on another platform (by replacing windows-specific stuff with linux-specific stuff).

---

### Post by bluesonic1 on 2009-06-09
actually only 1-2 persons contribute.. because no one wants to help.. or/and there aren't many linux users

---

### Post by Vadi on 2009-06-09
You have to know programming to do this. So if you got 100 linux users and 1 that knows how to program in C# and Mono, you'll only get 1 person working on it :P

So as for spreading the word, say that you need ppl who can program in Mono. porting win32 to linux is a bit wrong

---

### Post by Chronon on 2009-06-11
You could say that you're trying to make a clone of this game.  As Vadi says, "port" is kind of a misnomer in this situation.

---

### Post by Sockerdrickan on 2009-06-11
> **Bölvaður said:**
> it's pretty simple if it is a simple game.

Just compile the source and see what bugs you get (it is better in my opinion than starting to try to find common differences)

a common difference in c++ and other is using

#include <sys/time.h>
instead of 
#include <time.h>
This is not correct. The C standard defines <time.h> on **all** platforms. **Platform specific** time functions for Unix are available in <sys/time.h>.

By the way in C++ you would include <ctime> not <time.h>

---

### Post by HellionDarkLord on 2009-11-29
I too want to know how to port/clone games.  What do I have to know? where do I start?  I have autism so I can learn computer things really fast but lack in social understanding.

I want to know how to do this!!!  If Ubuntu ran all the games that Windows 7 ignores then Ubuntu would rule even more.

---

### Post by Vadi on 2009-11-29
To start off, you have to have the game's source code :\

---

