---
title: "How do you multiple word search with tracker?"
date: 2008-04-27
forum: Desktop Environments
---

### Post by shane2peru on 2008-04-27
Ok, the title just about describes it all.  I want to be able to do mutliple word searches with tracker.  I used to just use beagle for this feature, and I decided I would give tracker a try.  I looked on their home page and didn't see it.  I want to search much like Google does: 
"See Jack run"
  - it will search for that phrase, and only that phrase, or: 
Jack + Jill 
will give me all the results that contain Jack and Jill, if Jack is there and Jill isn't then it won't show me that.  Or:
Jack Jill ran
This will give me any document that contains Jack, Jill or ran.  This is how I want to be able to search with tracker.  Is that possible with tracker?  I was unable to find out how to do that.  Any ideas would be appreciated.  Thanks.

Shane

---

### Post by shane2peru on 2008-04-28
Ooook, I'm guessing there isn't much info out on this topic.  I wasn't able to find anything either!  Another question, how do I get in touch with the Tracker Developers?

Shane

---

### Post by stijngysemans on 2008-05-01
you contact them here
[http://www.gnome.org/projects/tracker/development.html](http://www.gnome.org/projects/tracker/development.html)

---

### Post by berteh on 2008-06-25
There is support for complex queries, maybe you can get some inspiration there:
[http://svn.gnome.org/viewvc/tracker/trunk/rdf-query-examples/](http://svn.gnome.org/viewvc/tracker/trunk/rdf-query-examples/)

moreover
from the README file:

  * "tracker-query" - this reads an RDF Query that specifies the 
  search criteria for various fields. It prints to STDOUT all 
  matching files. You can see some example queries in the 
  RDF-Query-examples folder. You can run the examples as 
  "tracker-query < RDFFILE"

  * "tracker-search SEARCHTERM" - this perfoms a google like search 
  using SEARCHTERM to retrieve all matching files where 
  SEARCHTERM appears in any searchable metadata

but i could find nothing about a google-like syntax.

---

