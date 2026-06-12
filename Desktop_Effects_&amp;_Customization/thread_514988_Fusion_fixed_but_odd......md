---
title: "Fusion fixed but odd....."
date: 2007-08-01
forum: Desktop Effects &amp; Customization
---

### Post by Immolatus on 2007-08-01
So I've got fusion running with compiz --replace. What I did was put a custom launcher on the panel. The problem before was that there were no window decorations, So I couldn't grab anything.
Just now I realized that the decorations disapear when I close the terminal that I ran compiz --replace in. So now if I want normal operation I have to leave that terminal open.

Not a big deal but this can't be right. Any thoughts???

---

### Post by arbulus on 2007-08-01
Instead of running the command in the terminal, hit Alt+F2 to bring up the "Run" box and then type  compiz --replace  in there.  You can close the run box and everything will still be running.

[edit]
What worked best for me:

```
compiz --replace -c emerald &
```

That seemed to work better for me.

---

### Post by hyperair on 2007-08-01
Or you can append an & to the end of the command. Then you can type "exit" to close the terminal.

---

### Post by Immolatus on 2007-08-01
> **arbulus said:**
> Instead of running the command in the terminal, hit Alt+F2 to bring up the "Run" box and then type  compiz --replace  in there.  You can close the run box and everything will still be running.

[edit]
What worked best for me:

```
compiz --replace -c emerald &
```

That seemed to work better for me.

I'm actually not using emerald. This is on a fresh install (never installed beryl or emerald), so the window decorations are metacity.

---

### Post by Immolatus on 2007-08-01
> **hyperair said:**
> Or you can append an & to the end of the command. Then you can type "exit" to close the terminal.

I'll try this and report the result.

---

### Post by Immolatus on 2007-08-01
:guitar:Brilliant!! You can put:

compiz --replace & exit

all in one command and it does all of it in a snap so I just got to push the button. nice.:guitar:

---

### Post by Immolatus on 2007-08-01
Sorry for posting so many, but I was wrong.
for what ever reason compiz --replace & exit works in the terminal but not from the custom launcher. whatever.

---

### Post by psyopper on 2007-08-01
THere's a couple of things to try. First I would suggest 
```
 sudo aptitude install fusion-icon
```

Then place a new "Program" in your session named Fusion Icon with a command of fusion-icon and set it to autostart with your session. 

There's also a really [cool little script]("http://ubuntuforums.org/showthread.php?t=489341") someone on the forum whipped up a few weeks ago and also works like a charm.

---

### Post by jhernandez1270 on 2007-08-01
Have you tried having Fusion run at startup?

in System>Preferences>Sessions
just add a new Startup program...Call it Fusion with the compiz --replace command

---

### Post by Immolatus on 2007-08-01
> **jhernandez1270 said:**
> Have you tried having Fusion run at startup?

in System>Preferences>Sessions
just add a new Startup program...Call it Fusion with the compiz --replace command

I'm afraid to, the last time I tried that X froze in a way I couldn't fix and I reinstalled.

---

