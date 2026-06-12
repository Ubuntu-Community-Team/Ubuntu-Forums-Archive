---
title: "Title bars distort, change color"
date: 2008-10-31
forum: Desktop Environments
---

### Post by geovino on 2008-10-31
I'm running 8.10 Intrepid and I'm noticing distortion on the title bars of all windows that open up whether Firefox or edit. the top bar with go half white instead of the solid brown tone. What would cause this? I've used four versions of Ubuntu and I've never seen this before.

Anyone else with this problem?

I have a Nvidia GeForce 5200 card. And the Nvidia glx 173 is installed.

---

### Post by ayyah on 2008-11-01
same problem here.
I think the new ubuntu theme has bugs because after i switched to clearlooks theme the problem disappears

---

### Post by phoenix_snake on 2008-11-01
make a bug report then, it happens on many nvidia cards.

---

### Post by commonplace on 2008-11-01
Same problem here, also on an nVidia card (Geforce 6150 Go, in my laptop) using the 177 drivers. Switching to ClearLooks didn't seem to resolve the issue for me.

/Kevin

---

### Post by geovino on 2008-11-01
Just changed theme to Glossy blue and it seems to be stable now. No distortion.

---

### Post by geovino on 2008-11-01
> **phoenix_snake said:**
> make a bug report then, it happens on many nvidia cards.

Where is the bug reports? Don't see it in the forum lists.

Try the Glossy blue theme, it's not distorting :)

---

### Post by phoenix_snake on 2008-11-01
> **geovino said:**
> Where is the bug reports? Don't see it in the forum lists.

Try the Glossy blue theme, it's not distorting :)
I said make a bug report

---

### Post by HIFH on 2008-11-01
Sounds like you've got [this bug](). Lots of people have it, myself included. It's apparently a problem with the nVidia drivers after a certain number, 177 and 173 are both affected. Earlier drivers without this problem aren't compatible with Intrepid.

The workarounds at the moment is either to use a non-Ubuntu made theme (ie. not Human, Human-Clearlooks or DarkRoom) or to disable Compiz. It's something to do with the combination of the Ubuntu themes, compositing and the nVidia drivers that cuase the problem.

Don't add another 'I've got this problem too' to the bug report, it has already been triaged, unless

[quote=Adam Del Vecchio]
Add new comments only if:
1. You have a Geforce 6 or 7 and you *don't* see the bug.
or:
2. You have *another* card then Geforce 6 and 7 and you *see* the bug.
or
3. if you have *new* information not included in the comments already posted (like the fact jbg7474 discovered that is dependent on compositing, not necessarily on compiz). For this last step, it requires that you read all the above comments (a pain, I know)

Thanks for helping.
[/quote]

---

### Post by kvanderslice on 2008-11-12
I've never made a bug report before, but I'm experiencing the same issue with a Nvidia Quadro FX card.

Can someone point me in the direction of writing a bug report on this?

Thanks.

---

