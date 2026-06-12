---
title: "Sound missing for non-sudo users"
date: 2006-04-21
forum: Desktop Environments
---

### Post by fm1234 on 2006-04-21
Hi,

sound works fine for the single sudo user I have. However, for the others, sound doesn't work. When I go to the volume control I get a couple of errors: the simplest one says:

No volume control elements and/or devices  found.

The other error window expands a bit on this message and suggests how to remove the volume control (!).

What can I do to fix this silly situation?

TIA,
Fernando Martins

---

### Post by louis_nichols on 2006-04-21
here's one thing you should check (please forgive if the option names aren't crrect, but I'm not writing from my pc and have n ubuntu available, so this is only from my memory): go to System>Administration>Users and groups then select each user and cick preferences. Under a tab called advanced, I believe, there is a list of user permissions, such as "use the web" etc. and one of them is "allow this user to use audio" or something like this. That should be checked and then things should be fine.

I had a similar problem once, and this is how I solved it.

---

### Post by fm1234 on 2006-04-21
Thanks louis_nichols, that was indeed it. I never though there would be permissions specific to perform tasks and much less for stuff like audio. Seems overkill.

Cheers,
Fernando

---

### Post by louis_nichols on 2006-04-21
well... that's Linux for you! ;)

glad it worked out.

---

