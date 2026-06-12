---
title: "Evolution opening 5 spamd childs"
date: 2006-01-04
forum: Desktop Environments
---

### Post by magnusbb on 2006-01-04
Hello,

Finally Evolution is sorting out my junk mail. But now, I have another problem. When Evolution calls spamd, it creates 5 child processes, and it's taking up a lot of memory. Can this be fixed?

---

### Post by esposj on 2006-01-04
I don't use Evolution, but wouldn't Evolution be calling spamc?

Spamd on my Debian mail server is called with the command line stored in /etc/default/spamassassin.  In there it is started with --max-children=5.

Hope this helps a bit..

---

### Post by dcstar on 2006-01-04
[QUOTE=esposj]I don't use Evolution, but wouldn't Evolution be calling spamc?

Spamd on my Debian mail server is called with the command line stored in /etc/default/spamassassin.  In there it is started with --max-children=5.

Hope this helps a bit..[/QUOTE]
The default spamd settings probably assume that it will be used for more than just Evolution checking e-mails, so reducing them may not be a problem - try it!

---

### Post by Coruba67 on 2007-05-28
wait wait wait.... how did you get evolution to start filtering spam.. that checkbox in the options does nothing and spamassassin is installed... how do you do this?  Its been driving me nuts, I have heaps of it coming through.

---

### Post by RAOF on 2007-05-29
That's the intended behaviour, presumably so that spamassassin can filter mails in parallel.  They shouldn't be using up too much memory, either, since almost all of the memory they use should be shared (memory usage statistics in linux tend to be a little bit misleading).

And in order to get spamassassin to filter mail, you need to flip a switch in /etc/default/spamassassin (I think).  There's an option which says "Enable", which defaults to "false" (or "0", I forget).  Once you set that to true (or "1"), and restart spamassassin, it should work.

---

