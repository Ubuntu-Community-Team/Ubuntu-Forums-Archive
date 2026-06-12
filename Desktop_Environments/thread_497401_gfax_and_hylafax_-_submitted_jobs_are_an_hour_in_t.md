---
title: "gfax and hylafax - submitted jobs are an hour in the future..."
date: 2007-07-10
forum: Desktop Environments
---

### Post by bazzer on 2007-07-10
Hi all
I've successfully set up and tested Hylafax on a server, and I'm happy with it. I can send and receive from Windows ok, using Winprinthylafax. So I added gfax on my PC (Edgy) and added the hylafax server. I can submit jobs fine, but when I check the box for 'Send Immediately', the jobs go in the queue on the server exactly one hour from 'now'. I've set the clocks on the server and my PC to the same time, so I'm not sure what's going on!
I've googled and read numerous FAQs but I'm still none the wiser as to where to start looking for the answer. I suspect it may be a BST / GMT issue, but where to go with that suspicion..?

---

### Post by JanvL on 2007-07-20
Start searching in the log-files.
/var/spool/hylafx/log
or something alike maybe you will find something.

Success Jan

---

### Post by bazzer on 2007-07-20
Thanks for your comment Jan, but it's not helped at all - the logfiles don't show any issues.

---

