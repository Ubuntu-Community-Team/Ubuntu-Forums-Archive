---
title: "how to get firefox to open this  	 git://github.com/artofmission/radiant-comments.git"
date: 2008-12-30
forum: General Help
---

### Post by Bartee on 2008-12-30
What do I set to get this to work ???

 	 git://github.com/artofmission/radiant-comments.git

I get this error message when I click on a link like the one above ....

---

### Post by kokkus on 2008-12-30
First of all, you have to add the protocol git://
Open a new firefox browser, in the address bar enter about:config
Right click, New, String.
The string will then be network.protocol-handler.app.git
And the value is the program you would like to open the git files with.
I don't know which file format git is but if it's an image or text file I suppose firefox will support it, so then the value will be firefox.

---

