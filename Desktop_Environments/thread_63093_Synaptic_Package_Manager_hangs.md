---
title: "Synaptic Package Manager hangs"
date: 2005-09-06
forum: Desktop Environments
---

### Post by kevmille on 2005-09-06
I installed Kubuntu and when I use the Synaptic Package Manager, it hangs after the below message:

[I]Setting up mailman (2.1.5-7) ...
Looking for enabled languages (this may take some time) ... done.

Looking for enabled languages (this may take some time) ... done.[/I]

Is this normal?

---

### Post by Mishura on 2005-09-07
I get something "similar" but instead Synaptic hangs when I click on the "Update List" button.  It will fetch all the packages and look like its done except.... its not done.  Everything is greyed out, and I have to "sudo killall -9 synaptic" to get rid of it.  My short-term solution was to do "apt-get update" from console before launching Synaptic.

Long term approach is to convert to Adept.  :)

---

### Post by kevmille on 2005-09-07
Thanks, I actually removed Mailman.  The hanging stopped after that.  I am too new I guess.  So used to Gentoo's Portage.

---

