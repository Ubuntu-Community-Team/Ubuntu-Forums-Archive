---
title: "What are the Windows / Linux implications of './configure'?"
date: 2009-03-21
forum: General Help
---

### Post by e_james on 2009-03-21
First I wrote FORTRAN programmes for an ICL 1900 computer; then I bought a Sinclair MK14 followed by Acorn System 2, Oric Atmos and TRS80 Model 4. For those machines I wrote both Basic and Hexadecimal code. The last processor for which I wrote assembly language was the Z80. I bought my first "IBM" PC in 1988 (640K, 40MB, 80286, MSDOS 3.3), moving up to MSDOS 4.0 in 1989, Windows 3.0 in 1990 and Windows 3.11 in 1994. I did some programming in Turbo Pascal and then Object Pal (Paradox) which I am still using.

The point of all the above is that I have some familiarity with computers generally and many years of practice with Microsoft Windows (3.0 - XP) and MSDOS. But I still have problems with Linux. At this time I would say that the fundamental issue is "default" behaviour which is the significance of the thread title. When someone explains something to me they must, of necessity, assume some common knowledge (e.g. English language), but I find that key details are often missing and these are commonly based on default behaviour. To further confuse the situation, I find that GNU/Linux is not just an operating system; it is also a culture - a way of thinking, leading to more default behaviours.

To illustrate the point of the title and probably my lack of knowledge - 

In MSDOS if I type the command "xyz" I will normally get the error message "file not found". If I remember the order correctly, the OS first assumes that the command is "built-in" like "copy" or "dir". It then checks the current directory / folder for an executable file of that name, (xyz.com, xyz.exe or xyz.bat) and finally it uses the "path" environmental variable to search other directories on the same basis. This rule is not the one that Linux uses. First Linux has no built-in commands; second it specifically does not search the current directory. This is the reason for the "./" in front of "configure"; it is a specific instruction to use the current directory. To an MSDOS user "./" is a strange and apparently unnecessary complication. To a Linux user it is a perfectly normal procedure.

At this point It may seem that I have answered my own question, but I have some more.

1. Is there a single location / web site / book or books where Windows and Linux default behaviours can be compared and understood?
If there is no current location which is suitable, would it be appropriate to start something and where?

2. If this thread would be better placed in another forum or some other location, I am open to suggestions (and help).

I can only spare 2 or 3 hours per week to learn about Linux and make any contributions which are within my ability.

---

### Post by sgosnell on 2009-03-21
I don't know of a 'comparison' site, but [this site](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224) is an excellent Linux tutorial.  If you can just forget the DOS, and just keep an open minde and learn Linux, it should help you.

---

### Post by The Cog on 2009-03-21
This site is a good reference:
[http://tldp.org/](http://tldp.org/)

Linux does have some built-in commands. Built into bash (the normal command interpreter). Use the command **man bash** for too much detail (but at the same time, not enough). 'q' to quit, '/' to search. 'echo' is a bash builtin command.

Not including '.' in your search path is normal behaviour for all unixes as far as I know. I'm pretty sure that's the case on Linux, hp-ux, solaris, OS-X, AIX, BSD, sys-V. As such, it was that way before DOS was ever written.

---

### Post by dcstar on 2009-03-21
> **The Cog said:**
> 
........
Not including '.' in your search path is normal behaviour for all unixes as far as I know. I'm pretty sure that's the case on Linux, hp-ux, solaris, OS-X, AIX, BSD, sys-V. As such, it was that way before DOS was ever written.

Requiring an executable command to either be explicitly stated or in a path is one way of reducing the possibility of running an incorrect command.

You may have the same name of a command (like an old version) in a particular directory - in DOS/Windows you can inadvertently run that command because you have happened to change to that particular directory, so that means you can get inconsistent results depending on what particular directory you are in. In Unix/Linux this "opportunity" does not exist.

Looking in the CWD in DOS/Windows for a command (by default) may be "convenient", but it does cause problems and is essentially just another example of the bad practice that has handicapped the DOS/Windows world for the sake of "convenience".

---

### Post by e_james on 2009-03-22
sgosnell

Thanks for the link. I have had a good look at the site and there is a lot of useful information. So far I haven't actually learned very much because generally the bits I understand are the bits I already know. I have no doubt that I could learn a lot about Linux from that site but it looks as if it would take me weeks of study.

Up to now my favourite comment about Linux instruction manuals is "Too Much Information, Too Little Explanation"; that site causes me to revise that statement (a bit).

I once used a Word Processor called TypeRite and I found the instruction manual to be ideal. For any function I wanted to use, I would read the relevant page and follow the instructions and it worked. I can't recall ever reading the same page twice.

I think it was John Steed (Patrick McNee) who said something like "You don't worry about the 99% which miss you, it's the 1% that kills you."

---

