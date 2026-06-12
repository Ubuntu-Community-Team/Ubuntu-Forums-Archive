---
title: "Ascii Colorization in vim/nano/pico"
date: 2009-04-08
forum: General Help
---

### Post by sonnychee on 2009-04-08
Hey Guys,

I've got a log file with embedded asci colorization.  A sample is shown below:

  ^[[4;36;1mProperty Load (0.000133)^[[0m   ^[[0;1mSELECT * FROM `properties` WHERE (parent_id = 73 OR id = 73) ^[[0m
  ^[[4;35;1mProperty Load (0.000146)^[[0m   ^[[0mSELECT * FROM `properties` WHERE (parent_id = 82 OR id = 82) ^[[0m

When these lines are cat'ed to standard out, the lines are nicely colorized in lavendar and cyan.  Is there any way to configure vim/nano/pico to do the same...or at the very least to auto hide all of the ascii color codes?

Sonny.

---

### Post by mb_webguy on 2009-04-08
Edit the /etc/nanorc file using either "sudo nano /etc/nanorc" or "gksu gedit /etc/nanorc".  Scroll down until you see a section called "Color setup".  This will include a number of lines like the following:```
## C/C++
# include "/usr/share/nano/c.nanorc"
```For each pair of lines, uncomment the second line (i.e. remove the "#").  Save and exit.  Now the next time you open any of the filetypes listed in /etc/nanorc, it will be colorized.  If you write PHP scripts, you might want to check out [this page]("http://wiki.linuxhelp.net/index.php/Nano_Syntax_Highlighting") for info about adding PHP syntax highlighting.

You'd have to do some Googling to learn how to do this with other editors.

EDIT: Actually, I misread your post the first time around.  I don't think what I suggested above will help your particular situation at all.  Sorry.

---

### Post by sonnychee on 2009-04-09
Hey WebGuy,

I need a way to render the "Ascii color" codes.  Syntax highlighting won't help me here...

Sonny.

---

