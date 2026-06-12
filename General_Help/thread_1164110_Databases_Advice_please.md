---
title: "Databases: Advice please"
date: 2009-05-19
forum: General Help
---

### Post by bill-linux on 2009-05-19
I need advice on a database. For years I've indexed all my files in a windows program called Endnote - I don't use the citation feature of Endnote (!), but just use it as a database. (That is, I'd never use it to generate citations on a paper, but would use it to find, say, "Where is that file that contains info about the guide we used in Rome in 2005? Oh, yeah, I put it in such and such a file.")

My problem: I'm starting some new project and will start a new database and don't want to use this Windows Legacy program, but when I turn to Ubuntu/Linux for a general database I find a) Something like SixPack that seems a bit under supported and focuses too much on being a bibliography generator, b) very rigid and under powered databases (the names escape me right now) or c) install mysql (or postgre) and build my own. I just don't have the time to do c right now ... so ....

Am I missing something: Is there some kind of Ubuntu frontend that lets you set up fields of your choice, runs mysql, and is pretty easier from a users viewpoint. I haven't found that .... perhaps I've missed it ... or more likely I don't understand databases well enough and such a thing just isn't possible.

Perhaps the emacs database bbdb would be a candidate ... since its emacs someone will maintain it forever. (This is true of any vi program also! No flames please: They are both lovely, lovely programs ....)

---

### Post by Cheesemill on 2009-05-19
How about OpenOffice Base. It's in Add/Remove programs.

Cheesemill

---

### Post by unutbu on 2009-05-19
mysql+phpmyadmin is another option.
phpmyadmin provides a web-based GUI for creating/updating databases and tables.

phpmyadmin is in the official repository.

---

### Post by bill-linux on 2009-05-19
This is wonderful suggestions ... I note I missed sqlite which has a GUI .... I will test this and other suggestions out and report back.

---

### Post by bill-linux on 2009-05-25
I guess I'm looking for something that just doesn't exist. It would be useful if someone would confirm it. I looked at all this tools - spending time with phpmyadmin and sqlite3 and sqlitebrowser. All seemed to be GUI tools (one web-based) to SET-UP a database - to set the fields, to define tables, or to execute SQL commands. Yet what I'm looking for it a frontend that pops up the field defined allows me to easily enter data and to search. In sqlite and sqlitebrowser, for example, to search I have to type SQL command, you know SEARCH * FROM ... blah, blah, blah. So is there no frontend - if that's the right word - or do I have to write my own. At this link [http://ubuntuforums.org/showthread.php?t=989714](http://ubuntuforums.org/showthread.php?t=989714) someone is looking for exactly what I'm looking forward. The responses seem to confirm that there isn't such a tool ... you gotta write your own. Maybe I'm missing something.

---

### Post by Tibuda on 2009-05-25
Try also [glom]("http://www.glom.org"). Never used it, but looks good.

---

### Post by unutbu on 2009-05-25
Is this what you are looking for?

To search:
In phpmyadmin, click a table in the left-hand panel, then click the Search button. Near the bottom is a form entitled "Do a query by example". Click in the text field and type in a keyword or number that you want to search for. Surround it with % signs to widen the search with wildcards. (% means 0-or-more of any character).

To enter data:
In phpmyadmin, click on a table in the left-hand panel, then click the Insert button. Fill out the form.

---

