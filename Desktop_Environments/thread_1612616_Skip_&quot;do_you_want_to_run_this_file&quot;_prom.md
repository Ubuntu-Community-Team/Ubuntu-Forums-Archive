---
title: "Skip &quot;do you want to run this file&quot; prompt and just open file with gedit?"
date: 2010-11-03
forum: Desktop Environments
---

### Post by tomdelonge on 2010-11-03
I hate double clicking a file and then having to click "display" to be able to start editing. This happens with .php, .py and even .html (I'm sure with other file types too). I'd like these files to not have a prompt when double clicked and just to open with gedit.

---

### Post by SlugSlug on 2010-11-03
try remove the executable flag from them ?

---

### Post by endotherm on 2010-11-03
the problem is that all of these are "executable" files, so if you proceed as you have described, you could never run a python script, unless you use the terminal. if you are fine with that, right click on a .py and select "open with Another application" and select Gedit. if the "remember this choice" box is checked, you should not longer be prompted for .py files. repeat for php//html. hopefully your web browser will still work...

---

### Post by tomdelonge on 2010-11-03
@endotherm

I tried doing that, but it still prompts to be run.

The only way I would want to run php or py is from the terminal anyway.

---

### Post by stinkeye on 2010-11-03
nautilus edit > preferences > behaviour
and choose your handling of executable text files.
If you want to run a script you can just drag and drop it in the terminal.
I let kupfer (similar to gnome-do) catalog my scripts folder and use it to run scripts.

Other types of non-executable files (eg html) should work how **endotherm** described.

---

