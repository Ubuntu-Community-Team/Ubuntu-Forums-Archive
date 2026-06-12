---
title: "emacs no longer accepts scim/skim input methods"
date: 2009-02-10
forum: General Help
---

### Post by bhrgunatha on 2009-02-10
I am using Kubuntu Hardy. 
I have emacs-snapshot installed from the ppa.launchpad.net repository. My default locale is en_GB.UTF-8 but I use scim/skim for writing Chinese.
Until recently emacs worked fine with scim I was able to use it to enter Chinese text - particular inportant to me are the ZhuYin characters. 
There was an update to the emacs-snapshot recently and co-incidentally I had to reboot my desktop machine for the first time in a few weeks.

Now I am no longer able to use scim to enter Chinese text in emacs.
Scim is working fine for example with Kate and firefox.

Does anyone have any ideas why it has stopped working and how to diagnose or fix the problem.

---

### Post by nenjordi on 2009-06-19
Try installing emacs-snapshot-nox, to use it the comand is emacs-snapshot-nox instead of emacs.
If it works you can uninstall emacs and dpkg-reconfigure emacs-snapshot-nox, so it become the standard option.
It worked for me. Hope it's usefull for you.

BR

---

