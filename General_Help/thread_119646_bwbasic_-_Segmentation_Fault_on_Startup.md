---
title: "bwbasic - Segmentation Fault on Startup"
date: 2006-01-19
forum: General Help
---

### Post by demibee on 2006-01-19
I finally got around to installing the Ubuntu Hoary discs I received in the fall, and I'm impressed so far.

I made sure I had C, Perl, Python, and a few shells; but coming from a DOS environment, I wanted an old favourite -- gwbasic.  From what I've read on the Web, Bywater Basic (bwbasic) seems to fit the bill.  Plus, it's available on the Ubuntu Packages site for Hoary (bwbasic 2.20p2-5).

Unfortunately, it crashes on startup -- segmentation fault.  The only patches (and other versions) I could find for Ubuntu were in the Breezy section, and I'm reluctant to install that (it requires a version of libc6 that doesn't work with Hoary).

Does anyone know of a fix for this problem?

db

---

### Post by stream303 on 2006-01-20
I know this is kind of a weak reply, but I could never get bwbasic (with patches)  to remain stable on many of my machines either and I can't offer any specifics about how to fix it.

My favorite GPL'ed alternative that is *still actively supported*, is **BAS by Michael Haardt:**

[http://www.moria.de/~michael/bas/](http://www.moria.de/~michael/bas/)

The latest is ver 1.9.

I've always wondered why distributions don't include this GPL'ed basic.  Maybe because it emulates the old "microsoft" basics more accurately than any other I've seen.

You do have to compile it though  (ie the standard
./config
./make
./sudo install

So you'd also have to install the GCC compiler to create it..

I kind of detest answers that merely advise you to switch, but in this case, while we're waiting for BwBasic development to pick up (not likely!) this might suit you - check it out!

---

### Post by demibee on 2006-01-20
Thanks for the suggestion.  But I gave bas-1.9 a try a few nights ago, and it wouldn't compile... pages of error messages -- missing declarations, undefined references, etc.  (I don't mind delving into my own code, but trying to slog through that of others is frustrating.)

[ On another note, I installed "yabasic," but it's non-standard -- C-like while loops, for example... "while (n < 11)" instead of "while n < 11". ]

db

---

### Post by stream303 on 2006-01-20
Ok, how about my second-favorite: Chipmunk Basic

(free, still actively developed, but not gpl unfortunately.  I have run it successfully on Palm, Windows, Mac, and Linux)

[http://www.nicholson.com/rhn/basic/](http://www.nicholson.com/rhn/basic/)

Scroll down mid-page for the linux port.

I just downloaded it, extracted it to my home directory, and ran it as ./basic

I've used it for years and like how you can forego line numbering if you code in a text file rather than at the basic command line.

Like you, I've tried others, but nothing has come close to the old environments like BAS and Chipmunk Basic.

---

### Post by demibee on 2006-01-24
I gave bas-1.9 another go and managed to get it installed.  Despite the warning and error messages, the "make check" passes all tests.  Everything seems to work fine.  And you're right...  It's much like gwbasic... standard syntax and all.  Although I gotta admit, it's very weird to be able to place "#!/usr/bin/bas" at the top of the file and just run it! :)

Thanks again for your input.

db

---

