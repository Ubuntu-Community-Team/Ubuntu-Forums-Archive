---
title: "blank vim screen -- hide status etc"
date: 2009-03-25
forum: General Help
---

### Post by Cephi on 2009-03-25
I'm trying to figure out how to get my vim screen to be completely blank (sans my input, of course).  That is, I want to hide the status line at the bottom, and the tildes that follow the last line of the file.  

My searches have turned up nothing.  Any ideas?

Of course, once I figure this out, I'll also set it up so I can easily switch the status line etc back on.

---

### Post by evilaim on 2009-03-25
I, personally, don't think I've ever heard of such a thing.  If you were so inclined, I think vim is OpenSRC.  you could edit that and recompile it to hide and such, but I don't think there are options for that.

---

### Post by ibuclaw on 2009-03-25
1) You can't remove the tilde's from the application, but you can set their colour to match the same as the terminal background.

```
:hi NonText ctermfg=black
```
or if you have use a White Terminal, **ctermfg=white** and so on...

2) Don't think this is possible.

Best I could think of to match to this one is:
```
:set laststatus=0
```
Which is the default in vim...

If you want to see the alternative:
```
:set laststatus=2
```


Regards
Iain

---

### Post by Cephi on 2009-03-25
that's out of my league, evilaim, but maybe someday.
(1) done, thanks tinivole.  as to (2), i guess i could just resize the window so the status line is off the bottom of the screen... ha pretty ugly hack though.

---

### Post by ibuclaw on 2009-03-25
Actually ... there is one:
```
:set compatible
```
Removes the status line in vim, but it puts vim into "original **vi**" mode, so you may not find it the most friendly of user interfaces to handle.

Regards
Iain

---

### Post by Cephi on 2009-03-25
Ah perfect, thanks!  Already implemented.

Best,
Carl

---

