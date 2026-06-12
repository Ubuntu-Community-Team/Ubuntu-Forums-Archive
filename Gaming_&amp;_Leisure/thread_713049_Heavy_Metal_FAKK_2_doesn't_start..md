---
title: "Heavy Metal FAKK 2 doesn't start."
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by PsychoMan on 2008-03-02
I've installed game without problems with LIFLG instaler ( [http://liflg.org/?catid=6&gameid=68](http://liflg.org/?catid=6&gameid=68) ). 
But when I want to start the game (by typing 'fakk2'), it says:
> /usr/local/bin/fakk2: 29: Syntax error: Bad substitution

This is the line from the file:
> echo "${ll/* -> }"

Here is whole file: 
[http://ifile.it/q8drt0v](http://ifile.it/q8drt0v) 

I'm using Xubuntu 7.10. 
I would be very thankful for help.

---

### Post by Cappy on 2008-03-02
Find the path to fakk2 with
```
whereis fakk2
```
(this is the script you posted)

Now run
```
sudo sed -i 's+/bin/sh+/bin/bash+' /path/to/fakk2
```

or just edit the file by hand and change the top of the script from "/bin/sh" to "/bin/bash"

---

