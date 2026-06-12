---
title: "Problems creating an original Theme with animated Background for E17"
date: 2007-09-24
forum: Desktop Environments
---

### Post by darkmaster on 2007-09-24
Hello everybody, I'm using the latest cvs version of E17 on Ubuntu.
I created an original E17 theme with a static background and it worked.
I then created an animated background and it worked alone. 
I then tryed to put the animated background into my theme instead of the static background and I get this error:

sh build.sh
edje_cc: Error. default_background.edc:48 unhandled keyword collections

I don't understand why the background alone works and if inserted into the theme than the whole thing doesn't work.
To put the animated background into the Theme, I copied all of the background files (Except naturally build.sh) into the dir of the Theme and then setted in the default.edc file (The one that is compiled by build.sh) the default_background.edc file as the background. 

Now, the fact is that compiling default_background.edc alone worked and created an animated background usable with E17. Why can't it be compiled then togeter with the Theme?
Please, if you need further details ask me and I'll put everything out here.

---

