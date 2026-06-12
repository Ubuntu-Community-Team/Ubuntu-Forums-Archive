---
title: "Breach post mortem"
date: 2014-12-29
forum: Forum Feedback &amp; Help
---

### Post by bashiergui on 2014-12-29
Regarding this: [http://blog.canonical.com/2013/07/30/ubuntu-forums-are-back-up-and-a-post-mortem/](http://blog.canonical.com/2013/07/30/ubuntu-forums-are-back-up-and-a-post-mortem/)> The attacker used these shell kits to upload and run some custom PHP code to dump the ‘user’ table to a file on disk which they then downloaded.


Has Canonical released details about the custom PHP code?

---

### Post by deadflowr on 2014-12-30
I'm not sure.
Seems like something that they'd share with the vbulletin team only, since it's something that could effect how vbulletin works.
Canonical isn't like Security firms who relish in releasing info about code that can hamper various softwares, with udder disregard.
While they'd probably love to release all code, they do respect other software makers and try not to hinder their work.
At least that's my thinking on it.

---

### Post by bashiergui on 2014-12-30
Right. The way the Canonical blog post reads the custom php code wasn't the exploit. The initial xss post was, and that probably exploited a vulnerability that vbulletin needs/needed to patch. The custom php code was uploaded post exploitation and would give insight to the attacker. It was a tool used by the hacker which would probably be revealing.

---

