---
title: "colored text in gnome-terminal and terminator is highlighted strange"
date: 2009-05-26
forum: General Help
---

### Post by darkstarLNP on 2009-05-26
Why is my colored text highlighted like this ?  I cant figure out any way to make it stop.  I have tried terminator, gnome-terminal, also tried changing fonts, changing the terminal type, and removing the .bashrc file.  It doesn't happen in rxvt or xterm but there isnt any support for TTF with those.

Thanks for any help.

Oh and I am using 9.04.

Look at the screenshots for examples:

How my character info looks.
[IMG]http://i512.photobucket.com/albums/t329/asdf_blah/Screenshot-1.png[/IMG]

Output of ls /dev
[IMG]http://i512.photobucket.com/albums/t329/asdf_blah/Screenshot.png[/IMG]

---

### Post by darkstarLNP on 2009-05-26
Ok. Figured out the problem.  In gnome-terminal, go to profile preferences and then the color tab, change the Built-in schemes to Rxvt or xterm.  Viola!

---

