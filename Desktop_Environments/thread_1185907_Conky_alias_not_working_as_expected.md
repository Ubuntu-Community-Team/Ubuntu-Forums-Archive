---
title: "Conky: alias not working as expected"
date: 2009-06-12
forum: Desktop Environments
---

### Post by vrothdar on 2009-06-12
I've installed conky 1.7.1.1 from the Karmic repos so that I can make use of the alias config setting. I'm trying to create aliases for fonts, colours etc. that I use several times in my config file so that I can quickly alter the appearance of conky to suit new wallpapers.

For example, I use ${offset -15} at the beginning of each text line and ${offset -13} at the beginning of any line that starts with a bar. If I ever decide to change these it'd be nice if I didn't have to change every single line!

So I add the following lines before TEXT
```
alias text_offset offset -15
alias bar_offset offset -13
```

I replace ${offset -15} with $text_offset but get "offset -15" as text output. ${text_offset} does the same.

Adjusting the alias lines to
```
alias text_offset {offset -15}
alias bar_offset {offset -13}
```
or
```
alias text_offset ${offset -15}
alias bar_offset ${offset -13}
```
or
```
alias text_offset $offset -15
alias bar_offset $offset -13
```
doesn't work either.

---

### Post by y5005 on 2009-07-30
I have the same problem. Did you manage to solve this ?

---

