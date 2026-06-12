---
title: "gToDo - autostart"
date: 2009-02-26
forum: General Help
---

### Post by kneewax on 2009-02-26
I recently started using the gTodo tool for my todo lists.  It is small, well-featured, and easy to use.

The only problem I have is I cannot get it to autorun, and I can find no support for it online (is it a dead app now?)  Ideally if i could make it start minimized to tray that would be even better.

I have tried adding the command line to the Preferences>Sessions>Startup but it still won't start.

if I can't do this I may need to find a different manager - any recommendations?

---

### Post by Vadi on 2009-02-26
Didn't check out the autostart problem, but try Tasque?

---

### Post by pointydrip on 2010-02-25
I also use gtodo with several lists at startup.

Go to System>Preferences> Startup Applications

Click 'add'

In the 'Name' field give it any name you want

Under 'Command' type:

gtodo

If you want open a list you save with a different file:

gtodo -s /home/user/filename

in startup applications 'add' that command for how ever many file's you have, or make one bash script for it.

---

