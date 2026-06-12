---
title: "Why does terminal text color change?"
date: 2005-04-22
forum: Desktop Environments
---

### Post by mrtaber on 2005-04-22
OK, silly question.  I'm just not used to distros that get me up, running, and productive so quickly!  I have to nitpick about something.  When I run a normal terminal, the files are not color-coded; however, when I run a root terminal, they are.  Is this a bug or a feature?

Thanks,
Mark Taber :)

---

### Post by ignavia on 2005-04-22
[QUOTE=mrtaber]OK, silly question.  I'm just not used to distros that get me up, running, and productive so quickly!  I have to nitpick about something.  When I run a normal terminal, the files are not color-coded; however, when I run a root terminal, they are.  Is this a bug or a feature?

Thanks,
Mark Taber :)[/QUOTE]
 Mine color-codes them as a normal user too. You can turn color coding on and off on a case-by case basis with 'ls --color=never' or 'ls --color=auto'

If you want coloringa always on without having to type it every time, try:

alias ls='ls --color=always'

Unless there's a better way?

---

### Post by mrtaber on 2005-04-22
Thanks for the tips!  I'm wondering...I installed the nvidia drivers, and the gnome-clipboard-daemon.  Wonder if either of those had anything to do with the odd behavior?  I'm grasping at straws now... ;)

Mark

---

### Post by tread on 2005-04-23
I really doubt it. One possible reason may be:

If you kept the home directory from your earlier distribution, that may have set ls aliases in your bashrc file .. which would of course override ubuntu settings.

---

