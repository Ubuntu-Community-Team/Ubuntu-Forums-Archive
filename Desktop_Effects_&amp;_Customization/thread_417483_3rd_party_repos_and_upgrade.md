---
title: "3rd party repos and upgrade?"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by muguwmp67 on 2007-04-21
I've used 3rd party repos to install beryl and some other apps.  What is going to happen to these apps if I upgrade to feisty?  Will they all be 'broken' due to unavailable dependencies?

---

### Post by mgmiller on 2007-04-21
One of the first things update manager does is disable the 3rd party repos.  After it's finished, you go into package manager and turn them back on in Settings>Repositories and the 3rd party software tab.   Highlight the one you want to change and click edit  You will need to change the release from edgy to feisty.  Then just click the check box to enable it.  Or you can manually edit /etc/apt/sources.list.  I just had to do this for wine, googleearth and medibuntu repos.   Worked without a hitch.

---

