---
title: "[SOLVED] How to install new fonts in 8.10?"
date: 2008-12-02
forum: General Help
---

### Post by gldearman on 2008-12-02
Hi,

I have some truetype fonts that I would like to install.  None are in the repos.  I would like to make them available for all of the users on my system, not just myself.

The last time I did this was in an earlier release (Dapper, I think, maybe Feisty).  It was pretty easy then, just 

1) copy the file to /usr/share/fonts/
2) change its ownership to root
3) type $ sudo mkfontdir /usr/share/fonts/

That no longer seems to work.  Does anyone know how to do this?

Thanks

---

### Post by gldearman on 2008-12-02
OK, I managed to solve my own problem.  But, I'm going to go ahead and post a link to the solution as a response to my own thread, in case anyone else searches these fora looking for the answers.

You can find the answer at [wiki.ubuntu.com/Fonts](wiki.ubuntu.com/Fonts).  Just as a note, I *did* have to reboot after rebuilding the font information files.  Until I did, no applications appeared to be able to see my new fonts.

Thanks, all!

---

