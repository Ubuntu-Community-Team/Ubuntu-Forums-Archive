---
title: "Lost &lt;ESC&gt; key response! (combo with &lt;ESC&gt; is fine!)"
date: 2009-01-13
forum: General Help
---

### Post by kakyoism on 2009-01-13
With Vim, I just found that <ESC> does not switch me back from INSERT mode to COMMAND mode. Then I realized with some child windows that are supposed to be closed with <ESC> are not able to anymore. 

On the other hand, switching focus window or panel with <CTRL><ALT><ESC> or the like is still working, which means that the keyboard key is not down. 

Anybody knows how to solve this?

---

### Post by cb34 on 2009-01-13
maybe something you can set in the /etc/vimrc or ~/.vimrc file. but i wouldn't know why i would stop working like that??

found this:
[http://vim.wikia.com/wiki/Avoid_the_escape_key](http://vim.wikia.com/wiki/Avoid_the_escape_key)
and this:
[http://vim.wikia.com/wiki/Start_in_insert_mode_without_losing_your_escape_key](http://vim.wikia.com/wiki/Start_in_insert_mode_without_losing_your_escape_key)

dont know if this stuff will help you.. but i hope so. :)

---

### Post by kakyoism on 2009-01-13
I forgot to mention that it only happens with gnome environment.
If I switch to console F1 for example, <ESC> works perfectly in Vim.

And I should emphasize again, I can't even close a pidgin conversation window with <ESC>, which is supposed to work, correct?

Thanks.

---

