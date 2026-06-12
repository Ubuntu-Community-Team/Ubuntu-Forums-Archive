---
title: "MySQL Query Browser ends abruptly when adding a table"
date: 2006-08-13
forum: Desktop Environments
---

### Post by locoHost on 2006-08-13
I have MySQL running. I can admin it fine with MySQL Admin. I can connect to it fine with MySQL Query Browser. However, when I try to add a simple table with one integer field, then click 'Apply changes' MySQL QB abruptly shuts down. I apparently cannot add tables. Any ideas what's happening?

Thanks guys :-)

---

### Post by gmarton on 2006-08-18
I have the same problem. it also happens when you try to edit a table.
Launched mysql-query-browser from terminal and this is the erro it gives after it crashes:

> ** (mysql-query-browser:16751): WARNING **: requested widget 'charset_combo' with the wrong type
Segmentation fault

Downloaded it from the MySQL site:
[http://mysql.com/downloads/gui-tools/5.0.html](http://mysql.com/downloads/gui-tools/5.0.html)

Untarred it, change to directory, it will ask you to update paths but it does not crash.

---

### Post by bijoux on 2006-08-18
i get the same error. i posted the same question everywhere including on mysql forums but i didnt get any answers.
i had no choice but to use the windows version under wine which works just fine. goodluck.

---

### Post by gmarton on 2006-08-18
I downloaded the linux version, that works as well.

---

### Post by locoHost on 2006-08-19
Are you saying if I download MySQL/QB from the MySQL site the "closes abrubtly on table edit" error goes away?

---

### Post by gmarton on 2006-08-19
Yes, I downloaded the "Generic x86 Linux TAR (bundled dependencies)" untarred it, then run it with  ./mysql-query-browser from the directory that I extracted to. It asked to run it once with --update-paths, then it works.

---

### Post by vice on 2006-08-29
> **gmarton said:**
> Yes, I downloaded the "Generic x86 Linux TAR (bundled dependencies)" untarred it, then run it with  ./mysql-query-browser from the directory that I extracted to. It asked to run it once with --update-paths, then it works.

I'm currently running on Ubuntu 6.06
I installed the mysql qb with synaptic
There was no problem encountered when running qb
However, qb abruptly exits when clicking apply changes.

I downloaded the tar file and extracted it to one of my folders.
Then i ran:
    ./mysql-query-browser --update-paths 
... as you advised in your post.
Terminal message reads:
    Updating mysql-query-browser installation paths...
    Done.
I assumed this fixed the prob.
I ran qb and tried clicking on 'apply changes' but qb still exits.
Did I leave out a step somewhere?
How did you make yours work?
Pardon me for asking a question that you may already have answered.
:)

---

### Post by gmarton on 2006-08-30
It does not actually fix the version installed by synaptic, it is just an alternate solution until the synaptic one gets fixed.
Run it with ./mysql-query-browser from directory you downloaded.

I added it to my gnome panel as a custom application launcher.

---

