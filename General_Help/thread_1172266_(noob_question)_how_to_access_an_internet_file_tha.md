---
title: "(noob question) how to access an internet file that is slightly wrong linked"
date: 2009-05-28
forum: General Help
---

### Post by LexLuthor08 on 2009-05-28
the url in my browser looks like this:

```
https://blackboard-app1.net.ethz.ch/webct/urw/lc4130001.tp0/cobaltMainFrame.dowebct?JSESSIONIDVISTA=pkz8KpPS9MgPGgt8lq2BPCy8mHRLtQ2FdKpK2dT7RQmd2KvB3Hb3!-1781457441!blackboard-app1.net.ethz.ch!80!443
```

you wont be able to access it since it requires a login

from inside this site I want to download a zip file. but it cant be found on the server. when I copy its link it sais:

```
javascript:showPage(-1, -1, -1, '/Visual%20System/Exercises/FilterTest.zip', 'WEBCT_NO_ANCHOR_VALUE', '3');
```

how do I have to modify the url to access this file directly? there must be some minor mistake in the link.

---

### Post by themusicalduck on 2009-05-28
Does it not just download if you click on it?

---

### Post by sahabcse on 2009-05-28
open the terminal then type

#wget -c [https://blackboard-app1.net.ethz.ch/webct/urw/lc4130001.tp0/cobaltMainFrame.dowebct?JSESSIONIDVISTA=pkz8KpPS9MgPGgt8lq2BPCy8mHRLtQ2FdKpK2dT7RQmd2KvB3Hb3!-1781457441!blackboard-app1.net.ethz.ch!80!443](https://blackboard-app1.net.ethz.ch/webct/urw/lc4130001.tp0/cobaltMainFrame.dowebct?JSESSIONIDVISTA=pkz8KpPS9MgPGgt8lq2BPCy8mHRLtQ2FdKpK2dT7RQmd2KvB3Hb3!-1781457441!blackboard-app1.net.ethz.ch!80!443)

---

