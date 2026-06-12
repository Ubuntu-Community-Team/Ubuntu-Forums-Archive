---
title: "Will I be stuck with using Windows Excel - Open Office Woes"
date: 2009-06-27
forum: Education &amp; Science
---

### Post by sukhiaatma on 2009-06-27
Hello every one,

I am a bio-inforamtics student.I am facing a rather "weird problem".

Until now I have not been able to find a alternative to Windows Excel

[INDENT][/INDENT] **The Reason**
[LIST=1]
[*]Have files with data entries/rows in excess of 65000
[/LIST]

Open office can handle files with rows up-to 65000 (I think with a patch. Cant confirm though)

"Please suggest a Alternative/'s"

---

### Post by Tibuda on 2009-06-27
MS Excel limit is also 65536 rows. If you have to manage a larger database, you should switch to a true database manager like:
Open source: MySQL, Firebird, PostgreSQL
Proprietary: Oracle, MS SQL Server

---

### Post by sukhiaatma on 2009-06-27
> **danielrmt said:**
> MS Excel limit is also 65536 rows. If you have to manage a larger database, you should switch to a true database manager like:
Open source: MySQL, Firebird, PostgreSQL
Proprietary: Oracle, MS SQL Server

They fixed that I guess..

[HTML]http://en.wikipedia.org/wiki/List_of_spreadsheet_software[/HTML]

---

### Post by leandromartinez98 on 2009-06-27
You probably should learn some programming language to deal
with that ammount of data, because using excel or its alternatives
will be painful. If what you want is doing graphs, try qtiplot
or xmgrace instead.

---

### Post by xadder on 2009-06-28
I agree about the programming - nearly always better than a spreadsheet for even small databases. Consider python+pylab(matplotlib).

---

### Post by InfernalNeutrino on 2009-06-29
xadder++ .... python + matplotlib = win.

I ran into this exact issue (the 65k line limit) once upon a time when my advisor asked me to debug some program I had never worked with before and I needed a fast way to spit out debugging information... it's really easy to parse text files containing the data with those tools. I actually pretty much stopped using spreadsheets after that because I realized just how much more capable an actual programming language is hehe. Cheers!

---

### Post by leandromartinez98 on 2009-06-29
Yeah, after learning programming you realize how inefficient and limited are spreadsheets.

---

### Post by hsweet on 2009-06-29
Plus there might already be stuff you can use.  I know there is a bio-perl project for genomics.  Holy large data set, batman!

---

### Post by sdbrogan on 2009-07-01
Gnumeric can be recompiled for more rows :

[http://projects.gnome.org/gnumeric/faq.shtml#5](http://projects.gnome.org/gnumeric/faq.shtml#5)

Not advisable though - 65 536 is already far too many

---

### Post by ahmatti on 2009-07-01
Also check R [www.r-project.org](www.r-project.org) and [www.bioconductor.org](www.bioconductor.org).

---

### Post by jbrefort on 2009-07-03
> **sdbrogan said:**
> Gnumeric can be recompiled for more rows :

[http://projects.gnome.org/gnumeric/faq.shtml#5](http://projects.gnome.org/gnumeric/faq.shtml#5)

Not advisable though - 65 536 is already far too many

Most recent development version of gnumeric (1.9.9) allows sheet resizing without recompilation up to 8388608 rows. But if there are enough data to fill all these rows, you need a huge available RAM.

---

