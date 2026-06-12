---
title: "Wine and perl?"
date: 2009-06-16
forum: General Help
---

### Post by wbest on 2009-06-16
Can wine run perl?
I've been looking for help getting it to run, but have got nothing.
So, is it even possible?
(Yes, I already asked in Wine, but nobody has answered, so I'm hoping-HOPING I can get an answer here.)

---

### Post by ManiacDan on 2009-06-16
Why are you trying to run Perl in wine?  Perl works fine right in ubuntu.

If you need access to windows-style filesystem commands, you won't get them from WINE.  Well, you will, but a better solution is an actual windows virtual machine.

-Dan

---

### Post by wbest on 2009-06-17
Well, I got it working.
But yeah, I need to make this great big set of C++ projects build in Linux.  I'm not sure of all of the different calls I need to handle, there are a lot...
I'm trying to port my company's set of projects, some rely on each other, some don't, to Linux.  There's too many calls to Windows API stuff, like Win32 to clean up on a case by case basis, so I'm hoping, as is my boss, to get it to work in wine.
 
I feel like using a virtual windows machine is missing the point.

---

### Post by sedawk on 2009-06-17
As long as the tools (e.g.Perl) use the windows API and do
not call any command line tools that are missing from Wine it
might work. But even if perl works it might depend on the
implementation of your perl scripts (e.g do they use "system" command?).

---

### Post by wbest on 2009-06-17
It only calls system once, as an xcopy call.
So I'm not sure how neccessary the line is.  I'll have to look into it and ask my boss.
 
Not sure about the C++ code its building though, can it call system?
I mean, I know java does, but I don't think its the *same* system...those commands work in *NIX systems after all.
 
It does make repeated refercnes to console, but that comes out of Win32, which I saw was in wine.   So will that all work?

---

