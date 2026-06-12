---
title: "No GNOME-shell or UNITY 3D after 12.04 upgrade"
date: 2012-06-28
forum: Desktop Environments
---

### Post by Kostya on 2012-06-28
Hello,

I have a bit of a problem and I can't seem to solve it. I upgraded from 10.10 to 12.04 2 days ago. There were no errors that I know of. Here is what's going on now:

1. When I login into Unity or GNOME (shell - not classic) I get blank desktop without any panels or toolbars. And there are no window decorations.

2. If I use GNOME Classic or Unity 2D - everything works.

3. If I create a new user and log in as that user, all desktop environments work fine.

4. In both, GNOME-shell and Unity, I can run "gnome-shell --replace" or "unity --replace" and all panels, toolbars and window decorations show up and appear to work fine.

Since everything works for a new user, I assume the issue is with some configuration setting(s) specific to my user account. I tried to rename .compiz* and .config folders but it didn't help. I tried to reset compiz settings (following someone's guide "to get your gnome panels back") but it didn't do anything. I tried "unity --reset" - nothing...

I am out of ideas.

Do you have any?

Thank you in advance.

P.S. I have ATI video. However, it clearly looks like a configuration of a user account issue and not a driver problem.

---

### Post by amadness on 2012-06-28
It may be that since Gnome-shell is not pre-installed in Ubuntu 12.04, it just won't work right. If you decide to reinstall, here's a couple of projects that combine Ubuntu and Gnome-shell:
1.[http://ualinux.com/](http://ualinux.com/)
2.[http://ubuntu-gs-remix.sourceforge.net/p/download/](http://ubuntu-gs-remix.sourceforge.net/p/download/)

---

### Post by Kostya on 2012-06-28
Thank you, amadness. 

Unfortunately, gnome-shell is installed and works for a new user account and for my user account if I start it with "gnome-shell --replace" It just refuses to start on its own. And Unity has the same problem.

---

### Post by fightling on 2013-03-12
same on my acer aspire one

---

