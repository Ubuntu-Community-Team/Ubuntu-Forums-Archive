---
title: "Two questions about Epiphany"
date: 2005-07-23
forum: Desktop Environments
---

### Post by manicka on 2005-07-23
Does epiphany have a websearch extension/toolbar like firefox's?

Can I import bookmark's into it from Firefox?

---

### Post by Knome_fan on 2005-07-23
[QUOTE=manicka]Does epiphany have a websearch extension/toolbar like firefox's? [/quote]
No, but you can just type something in the location bar and it will be looked up in google, for example.

[QUOTE=manicka]
Can I import bookmark's into it from Firefox?[/QUOTE]
Yes.

Have fun!  :grin:

---

### Post by charlieg on 2005-07-23
[QUOTE=Knome_fan]you can just type something in the location bar and it will be looked up in google[/QUOTE]
 To expand upon what Knome_fan said, the websearch functionality is built into the existing URL textfield rather than added as an additional toolbar component.  You just type your word and it offers a few options intsead of URLS for looking up that word on google or in a dictionary.  I'm not sure if you can add to these options with extensions but I'd be surprised if you couldn't.

Personally I prefer it the Epiphany way because it saves on space.

---

### Post by ow50 on 2005-07-23
In addition to searching with the URL bar, you can use search bookmarklets. For example, use the following as the address for a bookmark to do a search in Wikipedia.
```
javascript:q = '' + (window.getSelection ? window.getSelection() : document.getSelection ? document.getSelection() : document.selection.createRange().text); if (!q) q = prompt('Search Wikipedia for:', ''); if (q!=null) location='http://en.wikipedia.org/wiki/Special:Search?search=' + escape(q).replace(/ /g, '+'); void 0
```

---

### Post by horsefactory on 2005-07-23
There's a "Search the web" bar that functions like Firefox's, I don't recall exactly how I got it up, but try opening the bookmarks bar where I think it's put by default and then going to edit - toolbars and dragging it wherever you want it. 

[img]http://metawire.org/~ste/epiphanysearch.png[/img]

---

### Post by manicka on 2005-07-23
Thanks all for the tips and answers to my questions. :D

everything worked brilliantly

---

### Post by manicka on 2005-07-23
One more question. How stable is the epiphany beagle extension/plugin?

---

