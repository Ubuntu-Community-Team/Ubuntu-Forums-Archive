---
title: "how to set ld_library_path"
date: 2009-05-06
forum: General Help
---

### Post by gauthamk on 2009-05-06
hi everyone

      i am lookin into system call faliure ,so when i run the game tetravex it first looks into /usr/gnu and then into /usr/bin which is the right path so how can i set the correct path for an application using ld_library_path setting..... pls help

any suggestion welcome
 thanks in advance

---

### Post by slakkie on 2009-05-06
LD_LIBRARY_PATH is an enviroment variable, which you can set by doing this (depending on your shell):

export LD_LIBRARY_PATH=/path/to/libs


setenv LD_LIBRARY_PATH=/path/to/libs

You can put this in your .profile, or in your .bashrc or whatever rc your shell is using :)

---

