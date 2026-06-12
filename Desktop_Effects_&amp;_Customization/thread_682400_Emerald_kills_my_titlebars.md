---
title: "Emerald kills my titlebars"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by JakeWins on 2008-01-30
I found a couple of threads that were close to my problem, both here and on other boards, but none that was spot-on, and none that has solved my problem.

I just installed emerald and got me a fancy theme for my Ubuntu 7.10, running Compiz through fglrx. It worked fine for a while, but then suddenly the titlebars disappeared!

Running emerald -replace in a terminal fixes it, but as soon as i close that terminal (thus terminating the emerald process), they disappear again.

I ran "ps ax | grep emerald" and it returns nothing (except the grep process itself). Thus the problem aught to be that emerald for some reason terminates?

How do I start it back up w/out having to have that terminal running, or more preferably, is there any known fix to stop emerald from terminating in the first place?


Thanks in advance, and sorry if the issue has already been solved somewhere!

---

### Post by Tenken on 2008-01-30
You start emerald back up try this in a terminal, the "&" runs the program in the background so you can close the terminal or do other things in it.

```
emerald --replace & 
```

or his Alt+F2 and type emerald.

---

### Post by JakeWins on 2008-01-30
> **Tenken said:**
> You start emerald back up try this in a terminal, the "&" runs the program in the background so you can close the terminal or do other things in it.

```
emerald --replace & 
```

or his Alt+F2 and type emerald.

```
emerald --replace & 
``` Works just like it's supposed to - but oddly enough the process still terminates when I close the terminal!?

Is the process still "connected" to the terminal in some way when I use "&"?

Alt+F2 doesn't seem to do anything..

Thanks for your response though!

EDIT:I tried running "sudo emerald -replace &", and it worked like a charm! Granted, it loads the default settings for emerald since I configured it for my user, but that should be solvable.. Thanks Tenken!

---

### Post by Tenken on 2008-01-30
Yeah that was my mistake, the gnome-terminal is the parent process of the command(s) run in it. When you kill the parent process (terminal) the child process (emerald) is killed too.

---

### Post by Earl_Maroon on 2008-02-01
Cold it be to do with your settings in Advanced Desktop Effects Settings? There is a tick-box to enable/disable Window Decorations. Try that if the problem still persists.

---

### Post by rnazario on 2008-02-01
do you still have the X - and Maximize buttons? if not it might be a different problem with your drivers. If you do and the title bar looks buggy you need to play with the colors of the title bars in emerald. What video card do you have?

---

### Post by MaxwellGeekage on 2008-02-26
As rnazaria said, go to the advanced desktop effects settings. Go to the "window decorations" option and in the "command" box try putting -

 emerald -replace

I had the same problem and read this somewhere and it fixed it for me.

One more thing, how do you wrap code on this forum?

---

### Post by Islington on 2008-02-26
```
Like this?
```

---

