---
title: "Evolution time format"
date: 2005-10-28
forum: Desktop Environments
---

### Post by frenkel on 2005-10-28
Hi,

I'm new to Ubuntu, previously I used Gentoo, with Thunderbird for email. Thunderbird always respected my LC_TIME settings, so all times where in 24 hour format.
Evolution doesn't seem to care my LC_TIME=nl_NL, and displays it's date column in my inbox in 12 hour format. Somewhere in the settings I found how to change to 24 hour format, but that only affects my calander.
How can I change the date column of my inbox to use 24 hour format?

Thanks in advance,
Frank

---

### Post by frenkel on 2005-10-29
Doesn't anybody else have this problem?!

---

### Post by beow on 2005-12-16
With my thunderbird i did like this: First I checked which locales I had installed with "locale -a". Of these I picked the en_DK.utf8 that I know uses ISO8601 date format. Then I start thunderbird with

LC_TIME=en_DK.utf8 mozilla-thunderbird &

works like a charm with much nicer date/time display...:D

---

### Post by beow on 2005-12-17
Even better is to do like in another post... :???: 

In home directory, create file ".gnomerc". Edit it to contain
LC_TIME=en_DK.utf8
export LC_TIME

Supposedly all gnome applications will then give ISO date format.

---

### Post by a_dejot on 2006-11-15
first method (the one with the LC-change each startup) work but i cannot use the quickstart button that way. second method (.gnomerc) doesn't work at all.

so long,
a_dejot

---

