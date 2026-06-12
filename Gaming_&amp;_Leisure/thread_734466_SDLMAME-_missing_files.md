---
title: "SDLMAME- missing files?"
date: 2008-03-24
forum: Gaming &amp; Leisure
---

### Post by the2ndgenesis on 2008-03-24
Hey everyone. Just a quick question about missing files in SDLMAME.

When I queue up a ROM from my folder that is missing a file, the client doesn't tell me exactly which file is missing from the .zip... just that one is missing. Is there a specific way to find out which of the files are not present?

[added curiosity: I've changed my ROM directory more than once, and have found that "rom x" only seems to work in ONE directory, and not the other. What might be the cause of this?]

---

### Post by the2ndgenesis on 2008-04-07
Shameless bump :(

---

### Post by FranMichaels on 2008-04-07
The folder shouldn't matter as long as it is in the mame.ini, and matches (i.e. "roms" folder is not called "rom" or some typo)

As for missing files, make sure the roms are in the same folder, some may be dependent on a parent set (i.e. the japanese version is the main one, and the different stuff like for usa, europe, parts of asia depend on it.)

As for verifying your current roms

```
sdlmame -verifyroms
```

---

### Post by the2ndgenesis on 2008-04-09
Thanks Fran, that helps a lot!

One last question, though, and the answer is probably right in front of me: how can I determine what files a particular indivdual rom needs to run?

---

### Post by disturbedite on 2008-04-09
> **the2ndgenesis said:**
> One last question, though, and the answer is probably right in front of me: how can I determine what files a particular indivdual rom needs to run?
[http://www.mameworld.net/maws/](http://www.mameworld.net/maws/)

---

### Post by FranMichaels on 2008-04-09
> **the2ndgenesis said:**
> Thanks Fran, that helps a lot!

One last question, though, and the answer is probably right in front of me: how can I determine what files a particular indivdual rom needs to run?

You are very welcome. :)

A little bit of BASH will do the trick

```
sdlmame -verifyroms | grep "NOT FOUND"
```

You could also pipe it to a text file (if the folder you are in has write permissions)

```
sdlmame -verifyroms | grep "NOT FOUND" > missing.txt
```

If you mean just one set at a time, you can also do it this way if you prefer

```
sdlmame -verifyroms *whatever*
```
*replace whatever with name of romset, it will tell you what is missing, or if dependent on a parent rom

If you have a file but it says no good dump known, it's the best there is as of now (thus those changing sets...)

---

