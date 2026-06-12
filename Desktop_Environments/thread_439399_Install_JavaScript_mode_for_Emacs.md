---
title: "Install JavaScript mode for Emacs"
date: 2007-05-10
forum: Desktop Environments
---

### Post by Ferio on 2007-05-10
Hi, I've just downloadead a javascript.el and I wanted to use it with my Emacs, but I don't know any Lisp and all the solutions I've found using Google just don't work. Please, could anyone tell me just what I should do to use this JavaScript mode with my Emacs?

---

### Post by Bark on 2008-02-15
To install the JavaScript mode for Emacs, first obtain the Emacs lisp file at 

[http://joost.zeekat.nl/wp-content/javascript1.el](http://joost.zeekat.nl/wp-content/javascript1.el)

Then put that into a directory called "site-lisp" in your Emacs directories. If you don't know where that is, use "locate site-lisp" to find it.

Finally, in your .emacs file in your home directory, add the following lines:

(add-to-list 'auto-mode-alist '("\\.js\\'" . javascript-mode))
(autoload 'javascript-mode "javascript" nil t)

---

