---
title: "Database modelling"
date: 2005-12-22
forum: General Help
---

### Post by eztigma on 2005-12-22
Does anyone knows an ERwin like application to design databases in Linux?? I was thinking something Java.

Any thoughts?

---

### Post by BathroomNinja on 2005-12-23
Not off the top of my head, but have you checked over at sourceforge?

---

### Post by waster on 2005-12-23
Does ArgoUML do this? I seem to remember some java tools, but nothing packaged for debian.

---

### Post by eztigma on 2005-12-23
[QUOTE=waster]Does ArgoUML do this? I seem to remember some java tools, but nothing packaged for debian.[/QUOTE]

ArgoUML is a very nice CASE tool, but it doesn't support database E/R diagrams, and that's what I'm looking for. VisualParadigm's DBArquitect is not an option because it's not free.

---

### Post by bernardfrancois on 2005-12-23
Recently I have been searching this, because I had to do some school project (a database for a fictional library).

You can use **dia**, it has a set of UML graphs, but it's more oriented to programming; you can only set your fields as public, private and protected.
If you use dia, you can see the variable types in your scheme.
If you want to have code from your scheme, you can try tools like **dia2code** and **tedia2sql** (which I didn't try).

I also tried some other tools, but they weren't really mature. I don't know the exact names, I found all of this software in the repositories. I'm sure I tried **cogre** (which I didn't find useful), and maybe one of the other things I tried was **gaphor**.

Then, I discovered **umbrello**. It's an UML modeller for KDE, but synaptic will install the required packages to run it under gnome. There you can set primary keys, unique values, etc in the properties of each entity in the entity relationship diagram, but they won't show in the result.
But you can draw relations between entities, and add multiplicity.

In my search, I also discovered a very cool tool **graphviz**. All you have to do is to write some kind of script (which you can learn in minutes), and then give it to one of the console tools that come with graphviz. Each of the console tools will interpete your script in a different way (according to different algorithms of placing the nodes in the scheme).
For database modelling, you can use it to draw an ERD expressing relationships and entities (like in [this]("http://www.graphviz.org/Gallery/undirected/ER.html") example), but it's not handy if you want to be showing the fields of your tables or primary keys and stuff.

In the end, I chose for umbrello, and afterwards I added keys in the gimp. I have attached the final result.

---

### Post by SWAT on 2006-01-06
I'm also looking for a good database designer. I am used to [Sybase Power Designer](http://www.sybase.com/products/developmentintegration/powerdesigner), which is a really good program. You design a conceptual database model, then it creates a physical model. Then you just quickly check the physical model and then export it all to a certain database SQL code, like MySQL/PostgreSQL/Oracle etc. Then you just need to 'run' the SQL script file in your database and it will create all tables, relations etc. for you :D

For Linux I found programs like [Glom](http://www.glom.org/wiki/index.php?title=Main_Page) or [Mergeant (front-end for gnome-db)](http://www.gnome-db.org/). If anyone finds other programs, post it here!

---

### Post by briancurtin on 2006-01-06
i just looked at the power designer page and only saw an evaluation version for the full pay one. i know sybase has released some things here and there for free, is there a free version of this?**

**by free i mean free as in beer, not free as in someones registration key.

---

### Post by SWAT on 2006-01-06
[QUOTE=briancurtin]i just looked at the power designer page and only saw an evaluation version for the full pay one. i know sybase has released some things here and there for free, is there a free version of this?**

**by free i mean free as in beer, not free as in someones registration key.[/QUOTE]I guess not, since it's pretty expensive software.

What's the best free/GPL/open-source software available for database designing? I guess that's the more important question.

---

### Post by bernardfrancois on 2006-01-18
[QUOTE=SWAT]I found programs like [Glom](http://www.glom.org/wiki/index.php?title=Main_Page) or [Mergeant (front-end for gnome-db)](http://www.gnome-db.org/). If anyone finds other programs, post it here![/QUOTE]

Looking at the screenshots, it seems that you can't use **glom** to draw schemes. Did you try it?

I tried **mergeant**, but it doesn't detect PostgreSQL (I verified it's actually running, and I started the program after starting the Postgres daemon). I can't add nor select PostgreSQL to the list of 'providers'.
I also can't start drawing a database scheme. It seems that you will have to actually already create or edit a database while you're even still designing...
It also crashed once. Trying to use some options will pop up a window saying that the feature is not implemented yet. Apparently, it's still an early b&#232;ta version.

The tools I consider as more useful (for data modelling, not other tasks) are those that:
1) just let you draw a database scheme
2) don't necessarily have a code generation options
3) don't use the DBMS

So for now I still consider Umbrello as the best tool for database modelling (which is far from perfect, as mentioned before). Maybe I didn't find the right program yet, or maybe there's a vacuum that should be filled (If I had more time I would give it a try to create a light and specific program for database modelling).

Maybe a program could be written that creates a [.dot](http://www.graphviz.org) file for a database structure... I have exams now, and my studies make my spare time very small, so it won't be soon :( But I would like to try [glade](http://glade.gnome.org/).

---

### Post by luisg on 2006-02-08
Highly recommended: fabFORCE DBDesigner 4.

I have not installed yet in Ubuntu, but it works very well in that other OS :rolleyes: ...

---

### Post by obiwan on 2006-02-19
I like java tools for db modelling. Specially [druid]("http://druid.sf.net")

---

### Post by j0ney3 on 2006-02-21
[QUOTE=luisg]Highly recommended: fabFORCE DBDesigner 4.

I have not installed yet in Ubuntu, but it works very well in that other OS :rolleyes: ...[/QUOTE]

+1.  DBDesigner 4 is the best free one.  Too bad there's no .deb for it yet :sad:

---

### Post by SWAT on 2006-02-22
[QUOTE=j0ney3]+1.  DBDesigner 4 is the best free one.  Too bad there's no .deb for it yet :sad:[/QUOTE]DBDesigner 4 is dead. It isn't being developed further, they have stopped workin on it. That's a big reason for me not to use it.

I didn't know Druid, so I'll give it a try. Something I miss is a UML-like database designer for all sorts of databases (like Sybase PowerDesigner)

---

### Post by bernardfrancois on 2006-03-14
I think it would be easy to make a database modelling program using [**graphviz**](http://www.graphviz.org).

It looks like someone tried it: [http://savage.net.au/Ron/html/graphing-database-schema.html](http://savage.net.au/Ron/html/graphing-database-schema.html)

And here is a generated picture: [http://savage.net.au/Pictures/sweep.png](http://savage.net.au/Pictures/sweep.png)

I also found a list of database modelling programs on the same site: [http://savage.net.au/Ron/html/drawing-tools.html](http://savage.net.au/Ron/html/drawing-tools.html) . I didn't check if any of them can be used in Linux.

---

### Post by woooopa on 2007-01-30
Magicdraw looks pretty good.

:guitar: 

[http://www.magicdraw.com/]("http://www.magicdraw.com/")

---

### Post by peter07 on 2007-05-03
I'm also looking for such application, but I haven't found any good one yet :(

---

### Post by gabmunoz on 2008-02-22
Druid is a option that can make 'reverse engineer' with any jdbc, in this software is called 'export', getting all  pks and fks,  It can make a DER, save it as image or print. Has Folder to group your entities. Can execute code. 
The best is that its gpl and works very well.

In my case a need  make a der from a postgres 8.3 database. To make it a need to download java from sun, and jdbc4 from posrgres. It was easy.

---

