---
title: "Strange Warcraft III problem"
date: 2005-11-05
forum: Gaming &amp; Leisure
---

### Post by ltmon on 2005-11-05
Hi All,

I have installed my copy of WC3 under the latest wine (0.9) and it runs perfectly... full speed, sound etc.

I can play custom games and lan or battlenet games fine.

The only thing that won't work is the campaigns.  When I go to the campaign selection screen I get a level select (Normal/Hard), a back button and nothing else.  There are no campaigns to be seen.

Anyone had this problem?

Ideas to diagnose?

Cheers,

L.

---

### Post by ltmon on 2005-11-05
For future Googlers, see this:

[http://bugs.winehq.org/show_bug.cgi?id=2075](http://bugs.winehq.org/show_bug.cgi?id=2075)

In short, this is fixable if you don't mind patching Wine a little.

---

### Post by Takis on 2005-11-08
[QUOTE=ltmon]In short, this is fixable if you don't mind patching Wine a little.[/QUOTE]
And you can follow what they're on about. They suggest quite a few different things to do, in amongst the technobabble. Do you get what needs to be done...?

---

### Post by Takis on 2005-11-08
Okeydizzle what seems to have worked for me is:
[LIST=1]
[*]Get a copy of msvcrt.dll from Windows (located in C:\Windows\System32)
[*]Copy it into the windows/system directory of your Wine install.
[*]Open a terminal and run ```
export WINEDLLOVERRIDES="msvcrt=n"
```
[*]In the same terminal, run Warcraft 3 and create a new profile. You should be able to run campaigns.
[*]You can probably put steps 3 & 4 into a nice little script. Make sure to cd into the Warcraft III directory before running the program, it might not work otherwise.
[/LIST]

Notes:
[LIST]
[*]I don't really know how to use Wine. I'm just listing the steps that I did that worked for me. This may not necessarily work for you.
[/LIST]

Mods may like to move this post into the how-tos.

---

