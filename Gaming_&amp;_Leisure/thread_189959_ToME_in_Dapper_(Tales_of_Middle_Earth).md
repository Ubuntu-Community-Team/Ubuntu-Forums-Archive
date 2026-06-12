---
title: "ToME in Dapper (Tales of Middle Earth)"
date: 2006-06-05
forum: Gaming &amp; Leisure
---

### Post by J-Rod on 2006-06-05
Forgive the newbie question, but I am really wanting to get this running now that I've made the move to Dapper, and I am rather new to the *nix world.

It doesn't look like ToME is in the Dapper repositories, and I can't get it to compile from source. (make -f makefile.std give this error: -L/usr/X11R6/lib -lX11
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
make: *** [tolua] Error 1)

Has anyone gotten ToME running yet? Should I be trying to use old repositories? (It worked in Breezy)

---

### Post by J-Rod on 2006-06-05
I managed to answer my own question, apparently I didn't give myself access to enough repositories. I would still like to figure out how to get it to compile however, since I can't get mods running in it. It appears to be an issue with sudo, but I could be wrong. I wanted to try and install my own build in an area where I have full r/w privs for sure.

---

### Post by Perfect Storm on 2006-06-05
Did you have libx11-dev installed?

---

### Post by J-Rod on 2006-06-06
Nope, I sure didn't. I installed them and it worked fine. It makes sense that I'd need to have those dev files when compiling, it's just that I find it hard to troubleshoot when the *nix world is so new to me. Thanks for the reply, I am going to play with it and see if that fixes my issue with installing mods!

---

