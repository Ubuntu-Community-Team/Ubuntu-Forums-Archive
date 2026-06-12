---
title: "Nautilus vs. user environment"
date: 2011-02-21
forum: Desktop Environments
---

### Post by UBod on 2011-02-21
Hi,

I am using kile (and sometimes texmaker) to edit LaTeX documents. My private TeX style files are located in ~/localtexmf/ and I am using the TEXMFLOCAL environment variable (which I define in my ~/.cshrc) to tell kpathsea to search for files in this directory. If I call kile or texmaker from the shell prompt, I can use the kile/texmaker shortcuts to run LaTeX on my document (and it finds files in my localtexmf files as it should). If I open kile or texmaker by clicking the document's icon in Nautilus, kile (resp. texmaker) opens correctly and I can still run LaTeX as long as only standard packages (from the system-wide texmf directory) are used, but files in my localtexmf are not found. I found out that, obviously, Nautilus launches programs without passing the environment to them. I tried to find options in the Nautilus settings, but did not succeed. Maybe Nautilus is running in a different shell or it intensionally avoids using any shell.

My questions:
- Is there any way of passing my custom environment variables to application programs "through" Nautilus?
- If not, why not?

Thanks and greetings, Ulrich

---

### Post by UBod on 2011-04-02
I figured out a solution myself by the help of other forums. In case somebody stumbles across my posting, I am posting the - finally very simple - solution:

I added the necessary command to [FONT=Courier New]~/.gnomerc[/FONT]:
[INDENT][FONT=Courier New]#!/bin/bash

export PERLLIB=~/perl/lib/
export TEXMFLOCAL=~/localtexmf/[/FONT]
[/INDENT]That was it. It works nicely.

U

---

