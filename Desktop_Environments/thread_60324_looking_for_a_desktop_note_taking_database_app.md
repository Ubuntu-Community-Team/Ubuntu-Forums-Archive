---
title: "looking for a desktop note taking database app?"
date: 2005-08-27
forum: Desktop Environments
---

### Post by sal on 2005-08-27
anyone know of an app i can use for the following:

i need a database app to take notes in and be able to catagorize and search the notes when i need to. i also would need the ablitlty to add links (webpages, pdf, document, email, and the like) to local files and online files to the notes. 
i need to be able to back the notes up so as to be able to be easly imported back in in case of a needed data recovery.

if anyone can help thanks.

---

### Post by tom purl on 2005-08-27
[QUOTE=sal]i need a database app to take notes in and be able to catagorize and search the notes when i need to. i also would need the ablitlty to add links (webpages, pdf, document, email, and the like) to local files and online files to the notes. [/QUOTE]

Hmm... sounds like you need a simple web content management system (cms).  There are a lot of programs that fit the bill.  Here's some examples:

[list]
[*][Zwiki](http://zwiki.org/FrontPage) 
[*][Plone](http://plone.org) 
[*][Instiki](http://instiki.rubyforge.org/) 
[/list] 

If I were you, I'd try a [wiki](http://en.wikipedia.org/wiki/Wiki) tool with a small footprint.  Why?  Because wikis are easy to use and because it sounds like you want something that can run on your desktop.  Instiki's the best candidate for this, but Zwiki's footprint is also pretty small.

Most wiki's use a db back-end of some sort.  If the ability to do ad-hoc SQL queries is an absolute must, then you may want to look at wikis that can run on top of mysql or postgresql.  However, this typically means that you'll end up using a large program with an equally large footprint.  

All of the cms' listed above have built-in search engines, however, so you can probably use that instead of a third-party query client.

[QUOTE=sal]i need to be able to back the notes up so as to be able to be easly imported back in in case of a needed data recovery.[/QUOTE]

Instiki's the best for this.  It has a lot of backup options.  It's not too terribly difficult to do a hot backup Zwiki.  Google for "repozobackup.py".  

Each cms has it's own quirks, so I recommend googling for wiki and seeing which tools fits you best.  Good luck!

---

### Post by sethmahoney on 2005-08-27
Have you tried Tomboy?

---

### Post by sal on 2005-09-02
synaptic is asking to install a bunch of stuff along side it such as some dbus and mono stuff.
is this safe?

---

### Post by tom purl on 2005-09-02
[QUOTE=sal]synaptic is asking to install a bunch of stuff along side it such as some dbus and mono stuff.  is this safe?[/QUOTE]

What, are you afraid of installing a package that's named after a virus :)

You really shouldn't have any problems installing [mono](http://go-mono.org)  and it's related packages on your machine.  I installed them a while ago and it didn't break any other software on my machine.  

If you're worried about a virus, don't be.  Mono is Spanish for monkey; it isn't named after a virus.  

Have fun!

---

### Post by tom purl on 2005-09-02
Oh, and I forgot to mention.  Mono is a C#/CIL library.  Installing it on your machine is similar to installing any library/runtime (such as Java, Perl, or Python).

---

### Post by sal on 2005-09-03
[QUOTE=tom purl]What, are you afraid of installing a package that's named after a virus :)

You really shouldn't have any problems installing [mono](http://go-mono.org)  and it's related packages on your machine.  I installed them a while ago and it didn't break any other software on my machine.  

If you're worried about a virus, don't be.  Mono is Spanish for monkey; it isn't named after a virus.  

Have fun![/QUOTE]
 the only worry i had was that mono was still being developed.
i have my system set up just the way i like it and dont want it mucked up by anything.
as for the database thing its the only thing i have left to do to have my system set up just the way i want it.
let me ask you, will tomboy allow me to backup the database in case of system failure?

---

### Post by Reb on 2005-09-03
Tomboy stores all notes in the $HOME/.tomboy directory. It's a very good program.

---

