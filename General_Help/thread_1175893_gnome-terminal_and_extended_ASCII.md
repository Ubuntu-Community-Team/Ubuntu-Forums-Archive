---
title: "gnome-terminal and extended ASCII?"
date: 2009-06-01
forum: General Help
---

### Post by Vunutus on 2009-06-01
I'm trying to play a MUD via tintin++ running in gnome-terminal. The mud in question uses it's own font that replaces some nonstandard extended ASCII characters with small graphics/line drawing symbols. I cannot get this to work in gnome-terminal, though.

In place of every extended ASCII character I see a diamond with a question mark inside of it. I tried changing the character encoding of gnome-terminal but it didn't work. I tried almost every encoding that would make sense. Doing this got rid of the diamond/question mark but just replaced it with some other foreign character (but not the correct one).

---

### Post by Vunutus on 2009-06-02
Bump.

---

### Post by Vunutus on 2009-06-03
Bump.

---

### Post by Vunutus on 2009-06-04
Bump.

---

### Post by Vunutus on 2009-06-11
Bump.

---

### Post by rCXer on 2009-06-11
I've been wondering the same as well.  After an hour of googling I haven't found anything useful.  I think it would be a good suggestion for [ubuntu brainstorm](http://brainstorm.ubuntu.com/) :(

---

### Post by Vunutus on 2009-06-12
> **rCXer said:**
> I've been wondering the same as well.  After an hour of googling I haven't found anything useful.  I think it would be a good suggestion for [ubuntu brainstorm](http://brainstorm.ubuntu.com/) :(

Yeah, I googled for a while and found several people claiming to change their locale for it to work, and others claimed that other terminal programs like Konsole did it, but none of this produced the desired result for me.

---

### Post by Vunutus on 2009-06-13
Bump.

---

### Post by Vunutus on 2009-06-14
> **Vunutus said:**
> Bump.

Seconded

---

### Post by Vunutus on 2009-06-16
Time for another bump

---

### Post by Vunutus on 2009-06-17
Time for another daily bump...

---

### Post by Mindless Automaton on 2009-06-17
> **Vunutus said:**
> I'm trying to play a MUD via tintin++ running in gnome-terminal. The mud in question uses it's own font that replaces some nonstandard extended ASCII characters 

Its been my experience that mud clients usually don't supposed extended ascii.  (Assuming you mean characters from table 2 as seen here: [http://www.cdrummond.qc.ca/cegep/informat/Professeurs/Alain/files/ascii.htm](http://www.cdrummond.qc.ca/cegep/informat/Professeurs/Alain/files/ascii.htm))

Unless someone else knows and posts it, You are probably better off trying a telnet BBS client such as Syncterm. ([http://sourceforge.net/projects/syncterm/](http://sourceforge.net/projects/syncterm/))  Of course you don't have your usually mud-specific scripts and what not then.


:o

-Mindless Automaton

---

### Post by Vunutus on 2009-06-18
> **Mindless Automaton said:**
> Its been my experience that mud clients usually don't supposed extended ascii.  (Assuming you mean characters from table 2 as seen here: [http://www.cdrummond.qc.ca/cegep/informat/Professeurs/Alain/files/ascii.htm](http://www.cdrummond.qc.ca/cegep/informat/Professeurs/Alain/files/ascii.htm))

Unless someone else knows and posts it, You are probably better off trying a telnet BBS client such as Syncterm. ([http://sourceforge.net/projects/syncterm/](http://sourceforge.net/projects/syncterm/))  Of course you don't have your usually mud-specific scripts and what not then.


:o

-Mindless Automaton

Yes I believe those are the characters in question. I can't imagine why a mud client wouldn't support them, every mud client I used under windows (about 4-5 of them) supported the extended characters with zero tinkering. 

TinTin is the only MUD client I know of for Linux, and using a standard telnet client simply is not an option. A large majority of why I'm even playing said MUD is the scripts I develop for TinTin.

I've searched google extensively but every time I search for anything related to this, the first result is always this topic which means there cannot be much information out there =/

---

### Post by Vunutus on 2009-06-18
Time for today's bump

---

### Post by Vunutus on 2009-06-19
Bump.

---

### Post by Mindless Automaton on 2009-06-20
> **Vunutus said:**
> Yes I believe those are the characters in question. I can't imagine why a mud client wouldn't support them, every mud client I used under windows (about 4-5 of them) supported the extended characters with zero tinkering. 


Well other than BBS, I can not say I've played a mud that used extended.  Muds I've played use ANSI color, but not crazy little symbols.  In general muds are usually all about the text, so why support symbols?

Anyways, the code page is called:
IBM CP437 charset

If I run across anything else, I'll definately post here.

Thansk!

---

### Post by theozzlives on 2009-06-20
I used to do a lot of ANSI art, being an ex-sysop of a BBS. As far as I know extended ASCII disappeared with Windows 95.

---

### Post by Vunutus on 2009-06-21
> **Mindless Automaton said:**
> Well other than BBS, I can not say I've played a mud that used extended.  Muds I've played use ANSI color, but not crazy little symbols.  In general muds are usually all about the text, so why support symbols?

Anyways, the code page is called:
IBM CP437 charset

If I run across anything else, I'll definately post here.

Thansk!

I googled for IBM CP437 + gnome terminal and again the only relevant results were things I've posted =/

It's true that old school MUDs were all about text, but the MUD I play uses it's own font that functions more like a tileset than anything. It's possible to play without it but it's just not the same thing.

> **theozzlives said:**
> I used to do a lot of ANSI art, being an ex-sysop of a BBS. As far as I know extended ASCII disappeared with Windows 95.

The symbols I'm referring to work with zero configuration in every single version of Windows up to Vista and 7, why would you think they disappeared in post 95?

---

### Post by rCXer on 2009-06-21
Have you asked about it at the [TinTin++ forums](http://tintin.sourceforge.net/board/).  They probably know more than the people here?

---

### Post by Vunutus on 2009-06-21
> **rCXer said:**
> Have you asked about it at the [TinTin++ forums](http://tintin.sourceforge.net/board/).  They probably know more than the people here?

I hadn't asked there since I figured this was more of generic Linux question (or so I thought) than something Tintin specific, but I guess it's certainly worth a try. I'll make a post there later, thanks.

---

### Post by Vunutus on 2009-06-28
Shall I try another bump?

---

### Post by dandin1 on 2009-11-08
Whoops, posted at the wrong place.  Browser tab overload!

---

### Post by Vunutus on 2009-11-09
> **dandin1 said:**
> Whoops, posted at the wrong place.  Browser tab overload!

Aww and I was excited thinking that someone found my topic after all these months and had a solution 

I still haven't figured it out. I asked on the TinTin forums and the only solution they could come up with was some horribly complicated system of substitutions that would take hours to set up and probably wouldn't work anyway. 

I've tried gnome-term, konsole, xterm, and a couple other miscellaneous terminals like the one on my phone but the result is the same for all of them.

---

### Post by alphaniner on 2009-11-09
Have you seen [this]("http://kbase.redhat.com/faq/docs/DOC-17741") and [this]("http://osdir.com/ml/printing.a2ps.bugs/2008-08/msg00000.html")?

---

### Post by Kellimus on 2009-11-19
Has anything come of this?  I want to output the + extended ascii character (197, C5 in hex) for a simple Tic-Tac-Toe game I'm making in C++ and I downloaded the xfonts-terminus-dos but I'm still a 'noob' and don't really know what to do with it, or if it would even fix my problem...

I get a black circle with a ? in the middle of it, instead of the 197 + character when I "\xC5" in my cout in C++

I just want to make my program look better and not so yucky xD

Soooo....What else needs to be done to make it work, if it even works?

---

### Post by sinkr on 2010-06-08
See this article [http://nethack.wikia.com/wiki/IBMgraphics]("http://nethack.wikia.com/wiki/IBMgraphics").

I just went through the **gnome-terminal** instructions on Lucid and then was able to view the CP437 characters no problem.

---

### Post by Mindless Automaton on 2010-07-14
> **Vunutus said:**
> Aww and I was excited thinking that someone found my topic after all these months and had a solution 

I still haven't figured it out. I asked on the TinTin forums and the only solution they could come up with was some horribly complicated system of substitutions that would take hours to set up and probably wouldn't work anyway. 

I've tried gnome-term, konsole, xterm, and a couple other miscellaneous terminals like the one on my phone but the result is the same for all of them.

Yeah, that stinks that nobody has been able to help you out.  I haven't come across anything myself.

Do you still play the mud? (or read this forum :o) Give me the address and I will jump over on my gnome terminal and check it out. 

If they use their own font, do they supply a copy for users?  I'm guessing you got nowhere with the mud's forum (assuming there is one)..

Also, is the mud language english?  Maybe they are running another language the uses different characters?

Good luck!

---

