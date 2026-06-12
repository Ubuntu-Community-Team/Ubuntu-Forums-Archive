---
title: "Using a program as a widget in compiz fusion?"
date: 2007-10-05
forum: Desktop Environments
---

### Post by aridus on 2007-10-05
Hello
I have enabled the widget layer in compiz fusion on gutsy and am using some screenlets. But what I would really like to be able to do is to designate a particular program (other than screenlets) as a widget so that it appears on the widget layer (in particular Tomboy Notes). There is a place in the compiz settings manager to designate certain windows as widget but I don't understand how to use it - is this where I could add Tomboy, for example?
Thanks!

---

### Post by red_Marvin on 2007-10-13
If the window has a unique (sp?) title you can put **title=^TheTitle$** in the *CompizConfig->Widget layer->Behaviour->Widget Windows* textbox.
You also need the regex window maching plugin loaded.

---

### Post by aridus on 2007-10-13
Thank you!
I followed yr instructions using 'title=^Search All Notes$' (without the inverted commas) and then if tomboy is started with 'tomboy --search' I have Tomboy notes on the widget layer. The only problem I now have is that I would like this to happen at startup, but if I put 'tomboy --search' into the Startup panel of System -> Preferecnces -> Sessions it curiously does not stick (i.e. if I close and reopen Sessions it is not there, and hence tomboy will not start automatically on startup (I am using 7.10).
Any ideas anyone?
Thanks.

---

