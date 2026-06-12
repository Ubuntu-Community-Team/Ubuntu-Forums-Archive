---
title: "Libre Office Restriction in Bibliography Database"
date: 2011-02-18
forum: Education &amp; Science
---

### Post by zampes on 2011-02-18
Hi everyone,
I'm having a relatively minor problem with the bibliography database in Libre Office/ Open Office: When it comes to writing the "title" of a source, there's a 75-character restriction. The thing is that most M.A. and Ph.D. thesis titles are longer than 75 characters. Is there any way this limit can be extended to, say, 256 characters? I've been unable to find a solution in google... any help would be appreciated!

Thx.

-Zampes

---

### Post by zampes on 2011-02-18
Solved it myself. Here's how, if anyone's interested...
Follow this guide [http://wiki.services.openoffice.org/wiki/Documentation/OOoAuthors_User_Manual/Writer_Guide/Creating_a_bibliography]("http://wiki.services.openoffice.org/wiki/Documentation/OOoAuthors_User_Manual/Writer_Guide/Creating_a_bibliography")

Basically just open your bibliography database file (available in: /home/yourusernamehere/.libreoffice/3/user/database/biblio.odb) with LibreOffice Base, right click where it says "biblio" and change the "title" to be "memo longvarchar" so as to get a way higher character limit.

all set

---

