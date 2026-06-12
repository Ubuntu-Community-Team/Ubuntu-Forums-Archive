---
title: "how to produce colorful highlighting of python syntax via GNU Enscript"
date: 2024-03-21
forum: Desktop Environments
---

### Post by GwibberFooey on 2024-03-21
I would like to use GNU Enscript to produce a postscript file from a text file. The text file contains python code. The python code should appear with syntax highlighting in the postscript file. The highlighted (highlit?) syntax should by colorful rather than black and shades of grey. Here is the BASH command that I have tried:

```
enscript --highlight=python --color=true --output=output.ps input.py
```

Unfortunately the resultant file, output.ps, contains syntax highlighting in black and grey only. Question is: How to achieve colorful syntax highlighting? 


For the record: Ubuntu Mate 23.11 .

---

### Post by TheFu on 2024-03-22
If you haven't seen where syntax highlighting, count yourself lucky.  Usually it is very subtle. Nothing can replace the skeptical human when looking at code.

In testing formal code review outcomes, it has been found that humans will trust syntax highlighting more than they should.  There are times when the highlighting is wrong, but humans will ignore the error and think they made a mistake.

I worked in an SEI-5 software development process and while we were making excellent code with extremely few bugs, when we got syntax highlighting and added it to our reviews, the bug count drastically increased.  For a 20 person team,  together, we were introducing 1 bug every other year thanks to our review and development processes. After syntax highlighting was available, it became 3x higher.

Just another perspective.  Be careful for what you ask.

There is no Ubuntu Mate **23.11**.  [https://cdimage.ubuntu.com/ubuntu-mate/releases/mantic/release/](https://cdimage.ubuntu.com/ubuntu-mate/releases/mantic/release/)

---

### Post by MAFoElffen on 2024-03-22
I'm surprised that TheFu didn't answer this himself, since he is a vim diehard on using vim as an editor... Yes "us" old folks. LOL

In vim, with these two commands--
```

 :syntax

```
Turns on syntax highlighting...
```

:hardcopy

```
Prints it directly...
```

:hardcopy > %.ps

```
To print it to a .ps file.

There are other formats vim will convert to, such as HTML (with the colors), and .pdf.
```

:syntax
:%y
:TOhtml

```
and respectively
```

:syntax
:hardcopy > %.ps  | !ps2pdf %.ps && rm %.ps

```

There are also many other ways to do it, with other applications. But as TheFu mentioned, be careful what you ask for.

---

### Post by TheFu on 2024-03-22
Actually, I have never printed anything from vim/vi or any editor in decades.  In short, I didn't know the answer, but I still think it is a bad idea to trust syntax highlighting tools.

---

### Post by MAFoElffen on 2024-03-23
With CODE editors, what I find most useful is when they can recognize enough syntax to be able to collapse a structure. That in itself saves me a lot of time and frustration debugging when looking for typo's. Things just happen.

Of the features I look for in a CODE Editor:
Syntax
Error and warning marks
Auto code completion
Code snippets
Debugging
Extension ecosystem
Customization
Smart code navigation
Collaboration and version control
Community support
Document outline
Editor features
Find and Replace option
Intelligent source code compare
Speed

Under customization, the ability to create user macros. Sometimes it's just very useful to create a macro on the fly to automate something I need to change...

Also very useful, is the ability to turn on and off features on the fly! Sometimes code completion is evil and frustrating... (sort of like auto complete on phones.) When it thinks it knows better, what I want, when trying to read my mind. Yes, sometimes that gets in the way.

I have mainly used one CODE Editor for about 16 years = NoteTab Pro. I bought a license 16 years ago. It is well written and maintained by a Swiss company: Fookes  Software LTD. It only runs on Windows, but will run in Linux on Wine. It has a very large community following who have written many plugins for it. I highly recommend this editor. They do have a free version. The licensed version is well worth the money.

Next is the editor in Eclipse... Then, I hate to admit this, Microsoft's Visual Studio Code Editor... Each are powerful and have many features that make things easy for me.

I can do allot with just Gnome Editor or Vi... But why? I started out having to use EMAC's on mainframes. I have sentimental feelings for that, but things have evolved very much since then. Things are much simpler when you use a quality toolset.

The example is like: You can create a part you need for your car with a file and sandpaper. It will take some time, and the result will be limited, but it will work. It will keep you busy... Why struggle? Why skimp? Sometimes it's worth more than your time spent struggling. 

Be happy. Be well.

---

### Post by TheFu on 2024-03-23
I bought SPFEdit.  I've found a way to get nearly all features of spfedit (from the mainframe SPF environment) in vim.  Collapsing so only decision points are seen is handy.

However, since my coding style has matured since then and I don't have stupid stack limiting mandates anymore, I started writing functions/subroutines to be small enough to fit onto a single page - usually less than 35 lines, including comments.  Keeping functions small and easy for a human to understand is a core idea in creating bug-free code.  So really the editor doesn't matter.

I've never seen emacs available on a mainframe. Perhaps we have different definitions of "mainframe".  To me they are CDC or IBM systems running something like TSO.

---

### Post by MAFoElffen on 2024-03-24
@TheFu ---

My intro to 'mainframes' was in the service with DEC VAX 9000's running Unix (Ultrix-11). After getting out, then with real mainframes: IBM running VMS & CICS.

In the service, we were spoiled... Mainframe to workstation controllers that each had 4 Sony Trinitron's and very large optical disk-overs (with optical disks that where probably about 12" D) for the map overlays, Xerox Thermal Color printers and plotters, etc... then to terminals... About 1500 to 2000 interactive players, depending on the exercise. (Battle Simulations) That was my intro to Gaming.

That is where I first learned Unix, EMACs, then later XWindows. Later, they downsized to DEC VAX 8600, then DEC VAX 6460. That VAX 6460 was a super-mini the size of a small refrigerator, rather than compared to a whole room, and changed my outlook and opened my eyes on "how large" something had to be to do things. LMAO!!! In our tests, the 8600 couldn't keep up with it, even running in shadow as a backup.

I struggled with learning how to use EMACs. Everyone raved about it... I struggled with it. I constantly had this cheat sheet in front of me. To me, it was torture.

---

### Post by TheFu on 2024-03-24
In my book, anything running VMS or Unix is "mid-range".

My first Unix job, I used emacs, but my workstation, a DEC Alpha, only had 2GB of disk (or was it MB?) and that wasn't enough to have most tools natively compiled.  We used NFS for most of the storage, so my HOME was on a SunOS SPARC and I could run emacs on the SPARC, while I was compiling our team's software for the Alpha CPUs that our main client used.  This was a govt funded lab, so we had at least 1 of everything made and our software was required to run on all of them.  The job I had immediately before this one was on a JES3 TSO/ISPF mainframe doing cross compiling for specialized flight control computers based off the IBM-360.  I took a 360 ASM class where they use "DOS"  - nothing to do with PC-DOS or MS-DOS, it was an OS from the mid-1960s.  

Anyway, I used emacs daily for about 6 months, until I found myself switching to vi-mode almost constantly to get coding/work done.  Quickly, I stopped using emacs and started learning vi.  I've been learning a little more vim every day for 30 yrs.

There's vi for every platform I've seen from mainframes, through all midrange, PCs, and on every router I've used.  There isn't any other editor on many of those devices, so learning some vi is required.

---

