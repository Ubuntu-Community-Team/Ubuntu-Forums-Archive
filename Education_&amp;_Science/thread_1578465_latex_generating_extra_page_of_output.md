---
title: "latex generating extra page of output"
date: 2010-09-20
forum: Education &amp; Science
---

### Post by rajan on 2010-09-20
Hi, I'm making an equation sheet and I am having some minor problems with it. For some reason I am getting an extra page of output before the actual equation sheet. I don't know what is causing the problem, but I have never used the minipage environment before so it may be my inexperience with that. I am attaching the .tex file (named .txt because I cannot upload .tex files to this server) and the .pdf. 

I really would appreciate someone taking a look at this and letting me know what simple mistake I'm making. 

TIA.

---

### Post by FreeTheBee on 2010-09-20
Putting the minipage in a figure environment gets rid of the blank page, but it screws up the layout a bit. There must be a better fix around, but maybe this helps anyway.

---

### Post by rajan on 2010-09-21
thanks for the reply, i don't really know what i can do about this problem, but that figure environment idea may be the best option. or i could just not print the first page, but that seems like a hack-job to me.

---

### Post by xadder on 2010-09-21
Very odd. I couldn't get rid of that first page either. Maybe you should try one of the latex forums, where there are more latex-experts around.

---

### Post by rajan on 2010-09-23
please note the parallel thread running at latex-community.org ... i didn't want to spam the TUG email list and this seemed to be the most popular alternative. 

[http://www.latex-community.org/forum/viewtopic.php?f=46&t=10222](http://www.latex-community.org/forum/viewtopic.php?f=46&t=10222)

it's not "solved" but there's a reasonable solution. i just wish i could figure out why that minipage is being strange. thanks for all the replies.

---

### Post by Lateralis on 2010-09-23
If you want a two column document then you can use  

```

\documentclass[twocolumn]{article}

```

You can have whatever options in [] that you like.  We have to do this when writing papers.  The minipage environment can be a little strange but the above is well established and used.

---

