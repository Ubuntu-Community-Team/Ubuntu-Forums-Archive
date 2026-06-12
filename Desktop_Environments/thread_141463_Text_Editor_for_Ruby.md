---
title: "Text Editor for Ruby"
date: 2006-03-08
forum: Desktop Environments
---

### Post by scotoma on 2006-03-08
I installed Ruby on Rails and now I am looking for some good recommendations on a text editor for Ruby. One with syntax highlighting preferably. Any opinions out there?

---

### Post by colo on 2006-03-08
vim, of course.

---

### Post by soleblaze76 on 2006-03-08
Why not just use scite.  It works both on Linux and Windows.   [http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html)

---

### Post by scotoma on 2006-03-08
Yeah, I normally use vim, but it doesnt do syntax highlighting for ruby :-( Neither does gvim. Any other suggestions?

---

### Post by Keffin on 2006-03-09
[quote=scotoma]Yeah, I normally use vim, but it doesnt do syntax highlighting for ruby :-( Neither does gvim. Any other suggestions?[/quote]

Sure it does. Do you have "syntax on" and "filetype on" in your .vimrc? Do your ruby scripts have the extension ".rb" so that vim can realise it is a ruby file? If you don't want the .rb filename extension then there are ways around it, search for help about vims modeline and the filetype options. I just tried to quickly work it out and failed, but it can be done.

I'm sure I've done nothing special to get this. The vim package I have installed is vim-gnome, but I doubt that makes any difference.

---

### Post by Sendervictorius on 2006-03-09
If you wanted to go the whole hog, you could try the Eclipse Integrated Development Environment. There is a Ruby plug-in. 

Eclipse is awsome for developing Java apps, including Tomcat, and MVC frameworks (like Struts) and Object-relational mapping tools (Like Hibernate).

Although i haven't tried it, using the Ruby plugin should give you the same awsome features - things like intergated unit test, build tools, syntax checking, code completing, etc etc...


See this link: [http://www-128.ibm.com/developerworks/opensource/library/os-rubyeclipse/](http://www-128.ibm.com/developerworks/opensource/library/os-rubyeclipse/)

---

