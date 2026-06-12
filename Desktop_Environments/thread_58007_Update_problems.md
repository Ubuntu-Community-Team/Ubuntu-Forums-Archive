---
title: "Update problems"
date: 2005-08-18
forum: Desktop Environments
---

### Post by Terracotta on 2005-08-18
Hye, 
this isn't the first time encounter some problems when doing:
sudo apt-get update
sudo apt-get upgrade

It installs the new packages and all, but after the upgrade my cookies in konqueror are all gone, and now kopete doesn't want to sign in anymore, it doesn't do anything????

Can anyone help? And can anyone tell me why an UPDATE does these kind of things? aren't they supposed to fix problems, instead of introducing new ones? it's not the first time I might add, and I like kubuntu it's a great distro but this is more than annoying. Sorry if it sounds like a bash, a bit annoyed, is all.

---

### Post by daller on 2005-08-18
Well, it sounds wierd - never tried it myself.

APT is specially designed to avoid the deletion of any configurationfiles!

What you may be encountering, is that the updates requires a reconfiguration! (Not very likely though - Have you modified anything on your own in the kopete config-files?)

What did you upgrade from? (just a regular upgrade, or did you modify sources.list?)

I have upgraded a lot of machines - but never experienced anything like this!

---

### Post by arjaybe on 2005-08-18
[QUOTE=Terracotta]Hye, 
this isn't the first time encounter some problems when doing:
sudo apt-get update
sudo apt-get upgrade

It installs the new packages and all, but after the upgrade my cookies in konqueror are all gone, and now kopete doesn't want to sign in anymore, it doesn't do anything????

Can anyone help? And can anyone tell me why an UPDATE does these kind of things? aren't they supposed to fix problems, instead of introducing new ones? it's not the first time I might add, and I like kubuntu it's a great distro but this is more than annoying. Sorry if it sounds like a bash, a bit annoyed, is all.[/QUOTE]
 During upgrade APT will sometimes stop to ask you a question.  Did you answer 'yes' to any of those?

---

### Post by Terracotta on 2005-08-19
Not that I'm aware of. But I rebooted and it seems fine now, it's not like I installed a new kernel. Strange.
Thanks though.

---

