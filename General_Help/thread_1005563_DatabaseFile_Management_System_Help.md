---
title: "Database/File Management System Help"
date: 2008-12-08
forum: General Help
---

### Post by Jeff_Illingworth on 2008-12-08
Hello,

     I am an archaeologist and I am trying to set up a database to help manage and make accessible nearly 40 years worth of documents that have been published by our institution. Unfortunately, while I know what I want to do, I haven't a clue on how to do it and would appreciate any help.

     What I would like is a set-up where we can have all of our documents digitized in text-searchable PDF format. This collection of documents would be stored in some form of database that would be (eventually) web-based and searchable by author(s), date of publication, place of publication, key-word, and by text within the document. Ideally, this search would produce a thumbnail of the cover page of the result(s), the abstract, and a link to pull the whole document.

     I am sure such a thing can be built but, while I'm a wizard at digging square holes in the ground, I don't know much of anything about SQL, PHP, or any thing else. If anyone is familiar with a fairly turn-key program or suite of programs, I would appreciate hearing about it. Also, thanks for your time with, what I am sure, is a real "noob" of a questions.


Thanks,

Jeff.

---

### Post by cmnorton on 2008-12-09
If you have regular Ubuntu, you'll need to install LAMP. If you installed Ubuntu server, MySQL and PHP are already installed.

I would use a database to manage links (pointers) to the PDF files, rather than store the text and have to rebuild it on the fly. We have to keep certain tax/utility related documents and we don't use Informix to store the text. Instead, we keep the path of each document in the appropriate database table, and the actual zipped files are maintained in a directory.

---

