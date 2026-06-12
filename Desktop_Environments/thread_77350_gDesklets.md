---
title: "gDesklets"
date: 2005-10-16
forum: Desktop Environments
---

### Post by canadianwriterman on 2005-10-16
Is there any way to get a desklet to stay on the desktop so that, when you reopen Ubuntu, you don't have to place it on the desktop using the desklets item in the Applications menu? My weather desklet disappears every time I shut down.

---

### Post by akseli on 2005-10-16
[QUOTE=canadianwriterman]Is there any way to get a desklet to stay on the desktop so that, when you reopen Ubuntu, you don't have to place it on the desktop using the desklets item in the Applications menu? My weather desklet disappears every time I shut down.[/QUOTE]

Go to: System --> Prefereces --> Sessions --> Startup Programs
and add the command for gDesklets as you would type it into a terminal window or a run program (ctrl-F2).

That should do it

---

### Post by matthew on 2005-10-16
System --> Prefereces --> Sessions --> Startup Programs-->Add

gdesklets

Order: 50

---

### Post by mrmcctt on 2005-10-16
I just have a question about the order.  What is this for?  I haven't found anything on it and would like to understand better.

Thanks

---

### Post by canadianwriterman on 2005-10-16
Thanks to all of you. I'll try that.

---

### Post by matthew on 2005-10-16
[quote=mrmcctt]I just have a question about the order. What is this for? I haven't found anything on it and would like to understand better.

Thanks[/quote] This assigns a number between 1 and 99 which corresponds to the order in which this program will be run when Gnome starts. I just chose 50 becuase you are required to put something and it allows flexibility before and after.

This would be useful if, say, you had two programs and one depended on the other already running before it started.

You can also assign the same number to more than one program. I have gdesklets and gkrellm both set to run at startup, and both are assigned 50 as their order number.

---

### Post by mrmcctt on 2005-10-17
Thank You.  That cleared things up.

---

