---
title: "boinc project_attach command line only key ?"
date: 2006-09-12
forum: Desktop Environments
---

### Post by psyncho on 2006-09-12
If you, like me, are trying to attach to a project using boinc, and don't want to isntall a gui on your machine just to run it, then you have to get a key through a web interface on the project website.  Each project website is supposed to have a place to do this...which you can access by appending /create_account_form.php
to the end of its URL.

For instance, for climateprediction.net you can sign up online here:
[http://climateapps2.oucs.ox.ac.uk/cpdnboinc/create_account_form.php](http://climateapps2.oucs.ox.ac.uk/cpdnboinc/create_account_form.php)

Personaly, I couldn't find links to these things anywhere except for the einstein project which talked about needing it only for "legacy" clients (which I guess it means you're in the stone age if you don't have a gui).  I found this extremely annoying that ironically, the command line was powerless with this software and you had to have a gui to actually do something.  Usually the command line is more powerful.

---

### Post by TransitMan on 2006-09-12
It is called simplification.
If you are happier using the command line, by all means go for it.
But for simplicity, use the GUI in the BOINC client. Instead of starting BOINC by command line, start BOINC using "boincmgr". This will give you the GUI interface to input whatever info you need to attach to a project with. Once attached, you can close the GUI and restart with "boinc" command.
Happy crunching.

---

### Post by tribaal on 2006-09-12
I found my keys in the confirmation emails the various projects sent me.
Not sure about climateprediction though (I don't crunsh for this project).

The rest is a copy / paste thing :)

- trib'

---

### Post by psyncho on 2006-09-14
Yep, simplicity is great, that's why I wanted to use the command line :-)

I don't have any gui, no window server, nothing.  I have a server, that is meant to be a server, not a desktop, and I didn't want to put anything on it.

Thus, that "simple" solution of using the manager would have required me to install xwindows of some flavor, which I didn't want to do.  Thus, I put this hint here for others who were like me.  It actually wasn't a question, it was a solution.

---

