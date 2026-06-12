---
title: "Compiz: No focused window when switching viewports"
date: 2009-11-27
forum: Desktop Environments
---

### Post by tbraun on 2009-11-27
I am running Compiz (on Ubuntu 9.10 with Nvidia card). When I switch viewports, none of the windows in the target viewport will have focus. When I then switch back to the last viewport in which I did have focus, the focus will have been lost there as well.

The problem is exactly as described in [this bug here]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/95140"). That's from 2007 and ends with a note that this issue is fixed now.

But for me, in the latest Ubuntu, I still have that problem

Has anyone else seen this, or is there a setting I can fiddle with that might fix the problem?

Thank you very much...

---

### Post by tbraun on 2009-11-30
Hello!

Am I the only one with that issue?

I just found the raise-on-rotate option in gconf-editor. It was set to 'off'. After switching it on, it actually worked for about two seconds (I switched viewports and on doing so a window in the other viewport was actually focused). But then it stopped working again. Now toggling that flag does not have any further effect.

Please, anyone?

---

### Post by cerbero626 on 2010-07-08
This was really annoying me as well - I just found out how to fix it.
[LIST=1]
[*]Enable the compiz "Window Rules" Plugin in the CompizConfig Manager.
[*]Add a "No Focus" rule: 
```
type=Desktop | class=Cairo-dock
```
[/LIST]
Otherwise, the Desktop gets the focus when you switch to an empty workspace and keeps it after you switch back.

Tested on Kubuntu 9.10 32bit and Kubuntu 10.04 64bit

---

### Post by weaccept on 2012-01-20
What fixed it for me:

[LIST=1]
[*]Enable the compiz "Window Rules" Plugin in the CompizConfig Manager.
[*]Add a "No Focus" rule:
[/LIST]
```
type=Dock
```

Thanks for pointing me in the right direction cerbero626.

---

