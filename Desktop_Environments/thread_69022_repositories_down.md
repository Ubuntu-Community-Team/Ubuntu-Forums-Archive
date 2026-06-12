---
title: "repositories down?"
date: 2005-09-25
forum: Desktop Environments
---

### Post by rah on 2005-09-25
Uh, is it me, or are some of the repositories down at the moment?  I can't seem to find a whole bunch of them right now.... :-?

---

### Post by Galoot on 2005-09-25
Nope, it's not just you. It's been that way for at least the past few hours.

There are tons of [mirrors](https://wiki.ubuntu.com/Archive) still up, though.

---

### Post by rah on 2005-09-25
Well that's reassuring.

I thought maybe I'd somehow managed to break my system!

Thanks for responding. :)

---

### Post by Galoot on 2005-09-25
No problem. But there's no guarantee you *didn't* break something just because I can't connect.

...

...

...

What!? Don't look at me that way. I'm just trying to be helpful! :D

---

### Post by rah on 2005-09-25
Quite....

 :)

---

### Post by RadixLecti on 2005-09-25
Looks like the ftp are up.
Just change http: to ftp: in your repo-list

---

### Post by ounas on 2005-09-25
The [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) is down or is under some problem condition

**Mirrors can be found at:**
[Ubuntu mirrors](http://wiki.ubuntu.com/Archive) 

Use another mirror near to you, first make a copy of your sources.list with the following comment:

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**

then **sudo gedit /etc/apt/sources.list** to edit the file.

It worked for me

-
Ounas ;-)

---

### Post by ounas on 2005-09-25
[QUOTE=ounas]The [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) is down or is under some problem condition

**Mirrors can be found at:**
[Ubuntu mirrors](http://wiki.ubuntu.com/Archive) 

Use another mirror near to you, first make a copy of your sources.list with the following comment:

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**

then **sudo gedit /etc/apt/sources.list** to edit the file.

It worked for me

-
Ounas ;-)[/QUOTE]

You  can return back to the orginal sources.list when all is fixed!

-
Ounas :smile:

---

### Post by krak on 2005-09-25
changing http to ftp works
Thank u

---

### Post by installer on 2005-09-25
[QUOTE=RadixLecti]Looks like the ftp are up.
Just change http: to ftp: in your repo-list[/QUOTE]

This solves the current outage thanks.

---

