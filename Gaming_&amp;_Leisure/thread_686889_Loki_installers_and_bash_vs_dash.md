---
title: "Loki installers and bash vs dash"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by imakeart on 2008-02-03
Another gaming question from a newbie :)

I found the Loki installer for Cube and the installation went fine, but when I tried to run Cube I got the error:

 > Syntax error: Bad substitution

So I read the 'faqs' about the installer and saw this:

> I'm trying to start a game which I have installed using one of your installers and I get the error message "Syntax error: Bad substitution".
You are not using bash as your default shell. This is especially the case for Ubuntu users.
Open the relevant script and change the first line from "#!/bin/sh" to "#!/bin/bash".

But I read somewhere else that changing the shell could cause problems to other programs, so what am I to do?

Secondly, I have no clue where to find the 'relevant script' :lol:

I'm hoping maybe someone else has had to deal with this before and can please help me? Pretty please with sugar on top? :)

---

### Post by Darganot on 2008-03-08
this might be a day late and a dollar short, and it might not even be the right fix.  I know that for some of the other LOKI game installers and patches you have to use this syntax to execute:

> bash ./setup.sh

Instead of your normal sh then the filename.  So hopefully if you open a terminal in that directory and type

> bash ./yourfilenamehere

Hopefully the game should run.  If this doesn't help you it can help others with LOKI installers and patches for games like Alpha Cetauri or Railroad Tycoon 2.

---

