---
title: "Installing iBuild"
date: 2006-04-03
forum: Desktop Environments
---

### Post by Aulden on 2006-04-03
Hey everyone, 

Was wanting to try out ibuild ([http://ibuild.livecd.net/](http://ibuild.livecd.net/)) but can't seem to install it properly. I get the following message after the command 'sudo apt-get install ibuild'.
 
[B]The following packages have unmet dependencies:
  ibuild: Depends: python (< 2.4) but 2.4.2-0ubuntu2 is to be installed
E: Broken packages[/B]

What can I do? Has anyone used iBuild and suggest anything?

Thanks a heap!

---

### Post by hw-tph on 2006-04-03
It wants python of a lesser version than 2.4. Try installing 2.3: **sudo apt-get install python2.3**. It should not replace python 2.4 (you can have several different versions on your system at the same time), but I haven't tried this myself.


Håkan

---

### Post by Aulden on 2006-04-03
Thanks a lot for the reply.

I tried what you suggested but it said python2.3 is already the newest version.
Any other suggestions?

Thanks

Aulden

---

