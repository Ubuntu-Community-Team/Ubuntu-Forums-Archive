---
title: "Grass launches and then closes"
date: 2006-02-21
forum: Education &amp; Science
---

### Post by myotis on 2006-02-21
I have asked on the Grass list, but maybe some one here can help. I have installed Grass via the Ubuntu repostories.

Running it gives me the initial screen where you choose your mapset, but when I click on the "Enter Grass" button , the GIS manager opening screen apears briefly and the Grass closes completely.

I know this is ratehr vague but has anyine any idea what might be happening.

Many thanks,

Graham

---

### Post by celloandy on 2006-02-21
I'm not familiar with Grass, really, but try opening a terminal (in the Accessories menu) and running it from there (probably by typing "grass" and hitting enter).  This probably won't make it work any better than before, but it may spit out error messages onto the terminal when it dies, which may make it easier to diagnose the problem.

Andrew

---

### Post by myotis on 2006-02-22
Andrew,

Thanks for the reply.

If I run Grass from the terminal, this opens the same graphical interface, that you get when opening Grass from the Applications menu, If I click on the open grass button in the graphical interface, Grass Opens fine.

However, if I close it down and run it from the entry in the applications window, then I get the problem I described.

So there seems to be something different going on, between opening Grass from the terminal and opening it from the application menu.

I added Grass to the application menu using Smeg. Looking at this now I notice that I was running a command "Grass60" from the application, and the run in terminal tick box wasn't selected.

Changing the command line in Smeg to "Grass" and ticking the run in terminal option has got this working. I had assumed that as Grass ran in a graphics interface you wouldn't need to run the terminal.

However, now that I have it up and running, I know that some aspects are still command line driven and the only place you seem able to add commands, is in the terminal - so it looks as if this was the problem.

Thanks for pointing me in the right direction.

Graham

---

### Post by celloandy on 2006-02-22
Don't mention it.  Glad I could help.

---

