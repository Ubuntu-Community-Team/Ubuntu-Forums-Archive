---
title: "Why do I have to give my password several times ?"
date: 2008-01-06
forum: Desktop Environments
---

### Post by Little Ghost on 2008-01-06
Hi !
Eacht time I launch Ubuntu, it starts aith the default wallpapers, not with the one I've set. To   make it appear in the wallpapers list, I first have to open my HD (and give my password again), then to open the wallapers manager window, find the one I want and apply it.
Is there a solution for not having to enter so many times the same password, and to have the wallpaper I want allready on at launch ?

---

### Post by PeterJS on 2008-01-06
Having to enter your password multiple times, that's how the security system works, tasks that require elevated security privileges require that you reprove your identity with your password. I assume you're hard drive is an external, or secondary drive that isn't automatically mounting, or configured correctly at the moment to automount. So manually mounting the hard is something that only a super user can do so you need to enter your password for that to get elevated privileges.

Actually this sheds some light on why your settings aren't getting saved, if you open the wall paper manger with super user privileges which it doesn't need it will save your settings in the root account instead of your normal user account.

What happens if you right click on the desktop and select change desktop background?

---

