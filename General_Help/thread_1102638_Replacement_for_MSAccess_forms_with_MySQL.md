---
title: "Replacement for MSAccess forms with MySQL"
date: 2009-03-21
forum: General Help
---

### Post by rzj on 2009-03-21
I'm looking to find a way to replace sophisticated MS Access database applications.

MySQL is fine as the engine.
There are various report generators that seem to do the job of Access Reports (although any recommendations welcome ;)

I've found tools that handle database structure design including query builders, and db admin.

But what I want is a decent replacement for Access Forms - something that allows design of a decent dialog representation including list lookups for entry values, and allows the direct execution of update queries.

Is there such a tool?

Ideally something portable that could run on Windows as well as linux - not just Gnome or just KDE

I've seen PHP forms built into webpages but they don't seem to offer the same user entry experience and they are either hand coded or crude type-in-data for new record things.

TIA,
Ray

---

### Post by lovinglinux on 2009-03-21
It has been a long time since I used Access, but if you need a portable database I would recommend SQLite.

You can manage the database using sqlitebrowser

```
sudo apt-get install sqlitebrowser
```

or you can install [SQLite Manager]("https://addons.mozilla.org/en-US/firefox/addon/5817") extension for Firefox

If you need to design database forms, you could create them using bash scripts and zenity.

---

### Post by rzj on 2009-03-22
> **lovinglinux said:**
> It has been a long time since I used Access, but if you need a portable database I would recommend SQLite.

You can manage the database using sqlitebrowser


Thanks for the reply.

If I understand correctly SQLite is serverless. I want to host a database on a remote hosted Linux server and access it from windows desktops (and ideally Ubuntu desktops as well).

But I also want the rich UI features of a front-end like Access. I can achieve this by using Access on Windows as the front end to a MySQL server on the remote Linux server. 
But it locks me in to Windows desktop access if I want to reuse any of the client stuff.

I could write a load of code to build an application but I don't want to do that. I'd like to use portable and open tools but not if they can't do the job without a lot of extra work.

I'm not sure how much MySQL as the engine limits the effectiveness of the access tool-set - for example the query builder tools will generate MS Jet SQL rather than MySQL syntax so it may be that all of the wizards in Access will not work.

It seems odd that I cannot find an open source project to replace the useful aspects of Access in one place. I found report writers and db configuration front ends to MySQL but the only forms stuff seems to be simplistic web forms.

There are so many posts on so many sites saying "you can live without MS Word, Excel, Powerpoint and Publisher but not Access" and not having investigated this for a couple of years I was expecting that to have changed

Ray

---

### Post by ju2wheels on 2009-03-22
[http://www.openoffice.org/product/base.html](http://www.openoffice.org/product/base.html)

---

### Post by ju2wheels on 2009-03-22
[http://www.kexi-project.org/](http://www.kexi-project.org/)

---

