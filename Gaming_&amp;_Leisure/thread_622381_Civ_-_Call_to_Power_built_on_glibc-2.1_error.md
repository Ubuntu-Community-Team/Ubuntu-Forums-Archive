---
title: "Civ - Call to Power built on glibc-2.1 error"
date: 2007-11-24
forum: Gaming &amp; Leisure
---

### Post by Anafiel on 2007-11-24
Hi all!

I was running CTP on Fiesty just fine, but I did a fresh install of Gutsy, and CTP will no longer run.

I installed the game just fine, patched CTP to v1.1, and the game starts with no issues from term.  I can configure the game options and controls, but when I launch the map, this is the output in term:

***************************
anafiel@mudpuppy:~/Games/CivCTP$ ./civctp 
civctp: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.

BUG!  Assertion failed, cleaning up.
CivCTP Linux 1.1 Thu Jun 10 19:51:54 PDT 1999
Built with flags: 
-O2 -funroll-loops -fno-exceptions -fno-rtti -g -D_REENTRANT -DPACK=__attribute__ ((packed)) -DCIV3_SPECIES=75 -D_BFR_ -malign-double -D_SDL_STATIC_LIB -DSTATICALLY_LINKED 
Built with glibc-2.1
Please send the text of the failed assertion,
along with the contents of autosave to: [email]support@lokigames.com[/email]
*************************


Is the glibc version that this Loki game was built on the issue here?  What can I do to resolve this?

Thanks in advance for any ideas....

Anafiel

---

### Post by Anafiel on 2007-12-07
Hi again...

I was hoping that someone might have a little help for me here.  I'm not sure what the difference is between the Feisty and Gutsy distros, but CTP worked with Feisty...

Any ideas what might have broke my favourite Linux game?  [-o<


(Deus Ex is still my fav under Wine...)

---

