---
title: "Docbook 101?"
date: 2009-01-16
forum: General Help
---

### Post by pocketchange on 2009-01-16
I'm interested in maintaining more structured documentation for all my projects.  I've typically used Lyx in the past to create my documentation.  I've heard lots about Docbook, but know next to nothing about it.  

I'm curious to know these things:

[LIST]
[*]What are the best programs for creating Docbooks?
[*]What's the best tool for processing them into other formats?
[*]What tools and workflow are others using to create these?
[/LIST]

The last time I looked into this, I found things like Conglomerate, which is just an XML editor, extensions to vim, and export plugins for Openoffice.  It seemed like creating a Docbook required the use of so many different tools.  What's the best 1-stop shop for all Docbook needs?

---

### Post by pocketchange on 2009-03-04
I'm surprised to find nobody answered at all.  I'll answer my own question since I've been doing more research.

A good place to start for DocBook starter is here:

[https://help.ubuntu.com/community/DocBook](https://help.ubuntu.com/community/DocBook)

I would recommend reading the Definitive Guide to Docbook (package docbook-defguide is a bit outdated).  Try this instead:

[http://www.docbook.org/tdg5/en/html/docbook.html](http://www.docbook.org/tdg5/en/html/docbook.html)

It seems to me that the xml docbook is replacing the sgml.  I noticed in the newer versions of the definitive guide book, they just talk about xml and ignore sgml.  A good editor is emacs using the nxml-mode (sudo aptitude install nxml-mode).  This seems to be the best for writing the docbooks.

Anyone else have any further input?  Any better editors than emacs that work well in ubuntu?  I've tried some of the recommendations from the help.ubuntu.com article, but the interfaces are terrible.

---

