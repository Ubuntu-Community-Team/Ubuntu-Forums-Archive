---
title: "Evolution Mail freezes when I try to reply"
date: 2009-03-05
forum: General Help
---

### Post by thomas9129 on 2009-03-05
I am using Evolution 2.24.1, I haven't changed or updated anything recently.  It worked fine until a few days ago; now whenever I click on "reply" Evolution just freezes and turns gray.  I have to force quit and start over.  Same thing with trying to send a new e-mail.  I can receive and read e-mail without any problem.  I am using Ubuntu 8.10.

Any ideas?

---

### Post by dcstar on 2009-03-05
> **thomas9129 said:**
> I am using Evolution 2.24.1, I haven't changed or updated anything recently.  It worked fine until a few days ago; now whenever I click on "reply" Evolution just freezes and turns gray.  I have to force quit and start over.  Same thing with trying to send a new e-mail.  I can receive and read e-mail without any problem.  I am using Ubuntu 8.10.

Any ideas?

You can test if it is a config or data problem by renaming your (hidden) .evolution folder, then starting Evolution will create a fresh one.

If that fixes it you can manually copy all of your old data from the old folder to the new one, if not then there may be bigger problems elsewhere.

---

### Post by DrakeGis on 2009-03-08
I have a similar problem only when using encryption. So, maybe if you have PGP installed and configured, try to send an e-mail without sign it nor encrypt it.

---

