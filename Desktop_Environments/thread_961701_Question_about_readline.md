---
title: "Question about readline"
date: 2008-10-28
forum: Desktop Environments
---

### Post by Vorlin on 2008-10-28
[SOLVED]

Greetings all...I hope to fit in here somewhere and be of help perhaps, hehe. Right now, I'm currently running Ubuntu 8.10RC and I've currently run into a problem. I've installed apache just fine, same for php, as well as postgresql. The problem is when I try to psql to my database, I get this error:

$ psql pdb
/usr/lib/postgres8/bin/psql: symbol lookup error: /usr/local/lib/readline.so.5: undefined symbol: PC

Now when I do 'ldconfig -p | grep readline', here's what I get:

$ ldconfig -p | grep readline
	libreadline.so.5 (libc6) => /usr/local/lib/libreadline.so.5
	libreadline.so.5 (libc6) => /lib/libreadline.so.5
	libreadline.so.4 (libc6) => /usr/local/postgres8/lib/libreadline.so.4
	libreadline.so (libc6) => /usr/local/lib/libreadline.so
	libreadline.so (libc6) => /usr/local/postgres8/lib/libreadline.so
	libguilereadline-v-17.so.17 (libc6) => /usr/lib/libguilereadline-v-17.so.17

What could possibly be the problem and what can I possibly do to fix it so that it goes away and things work right? It looks like I've got all the right libraries but I have no idea what that undefined symbol PC is and why it's blocking me from psql and who knows what else. Thanks for any help in advance!

---

