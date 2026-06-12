---
title: "subversion-tools depend on exim4"
date: 2005-10-26
forum: Desktop Environments
---

### Post by mariuss on 2005-10-26
Trying to install subversion-tools prompts me to also install exim4, and this is very strange.

I have seen this for some other apps as well, can't remember which.

Any clues why is this happening?

One of the listed dependencies for subversion-tools is: exim4 | mail-transport-agent

Marius

---

### Post by geek.au on 2008-02-20
Some of the hook scripts will send email on check-in etc.. hence the dependency on an MTA

---

