---
title: "Finding .m3u~ files"
date: 2009-04-09
forum: General Help
---

### Post by GabrielWolff on 2009-04-09
I want to delete any .m3u file in a certain directory
Searching the forums I came to the conclusion that the best way would be with the GUI search option (and the "delete").
However, typing in ```
.m3u~
``` as a search request gives me no results, unlike ```
locate .m3u~
``` in the terminal, which gives me a whole pile of. 

How come? How do I work around this?

G

---

### Post by Michael.Godawski on 2009-04-09
hi GabrielWolff,

if locate does not work, I would try out the command "find" as described here:


[LIST]
[*][http://www.debuntu.org/how-to-find-files-on-your-computer-with-find](http://www.debuntu.org/how-to-find-files-on-your-computer-with-find)
[/LIST]
You can find anything you want and in the same step apply another action to the files matching your criteria.

---

