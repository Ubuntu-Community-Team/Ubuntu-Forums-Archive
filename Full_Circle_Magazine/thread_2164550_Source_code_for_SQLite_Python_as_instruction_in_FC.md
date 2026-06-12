---
title: "Source code for SQLite Python as instruction in FCM Special Python 1?"
date: 2013-07-31
forum: Full Circle Magazine
---

### Post by tridephysique on 2013-07-31
Hi everybody,
I am learning Pyhton myself following instruction in FCM Special Series Python. At the end of Part 7 of Volume 1, there is website to download source code [www.thedesignatedgeek.com]("http://www.thedesignatedgeek.com"), but the site is about healthcare, I cannot find any thing about Infomatics or Programing.
How can I get the source code?
Thanks.

---

### Post by oldfred on 2013-08-01
the source code is in the article and can be copied & pasted into a python file. Not quite as easy as downloading it, but it works.

 I use Geany, but do not use APSW. And I like to use sqliteman to review sqltables after I create them or other tasks directly. I use that to also test my sql code before copying into a python script.

Copy & paste into a python script. I copied sql from pdf and created this for just one table. You can then add the other tables. and queries.

```
#! /usr/bin/env python
# -*- coding: utf-8 -*-

import sys, threading, Queue, os
import sqlite3

def dbi(filename):
    create = not os.path.exists(filename)
    dbi = sqlite3.connect(filename)
    return dbi


def makeTable(tblname, sql):
    db = dbi(tblname)
    cursor = db.cursor()
    cursor.execute(sql)


sql = 'CREATE TABLE  IF NOT EXISTS Recipes (pkiD INTEGER PRIMARY KEY, name TEXT, servings TEXT, source TEXT)'
makeTable("cookbook1.db", sql)

```

---

### Post by gordintoronto on 2013-08-01
The web site is a .net, not a .com.

---

