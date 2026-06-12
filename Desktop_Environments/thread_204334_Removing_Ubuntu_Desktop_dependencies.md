---
title: "Removing Ubuntu Desktop dependencies"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Windrabbit on 2006-06-26
There are several programs that are dependencies of the Ubuntu-desktop package that I would like to remove (like Evolution, totem, and Rhythmbox). Is there any way to uninstall them without uninstalling the ubuntu-desktop package as a whole?

---

### Post by aysiu on 2006-06-26
No.

*ubuntu-desktop* by definition depends on the default packages in Ubuntu.

There's no harming in removing *ubuntu-desktop*... at least until before you upgrade to Edgy Eft.

---

### Post by jimravan on 2006-06-28
"There's no harming in removing ubuntu-desktop... at least until before you upgrade to Edgy Eft."

which is to say "There *is* harm in removing ubuntu-desktop".

Can someone explain why a specific email client is a dependency here anyway? Feels like somebody is making it hard for Ubuntu users to pick a different email client. Not a good impression for first-timers.

What Evolution packages can I remove if I have no intention of using the Evolution email/PIM application?

If instead I just remove everything Evolution and destroy ubuntu-desktop in the process, what do I have to do when I upgrade?

---

### Post by aysiu on 2006-06-28
[QUOTE=jimravan]"There's no harming in removing ubuntu-desktop... at least until before you upgrade to Edgy Eft."

which is to say "There *is* harm in removing ubuntu-desktop".[/quote] No. It's to say that between now and whenever Edgy's released (October?), you can remove *ubuntu-desktop* and be fine.

I don't see the need to remove something that I'm going to have to reinstall later in six months, so I don't remove it. I have a huge hard drive, and if there are apps I never use, I just delete the menu entry for those apps.

> 
Can someone explain why a specific email client is a dependency here anyway? Feels like somebody is making it hard for Ubuntu users to pick a different email client. Not a good impression for first-timers. As I tried to explain earlier, *ubuntu-desktop* is **not** a real package. It's a fake package that just points to the default packages of a Ubuntu installation. Evolution is the default email client for Ubuntu.

> 
If instead I just remove everything Evolution and destroy ubuntu-desktop in the process, what do I have to do when I upgrade? You're not "destroying" anything. As I said before, *ubuntu-desktop* is not a real package--it's just a pointer to other packages. Now, Evolution, on the other hand, *is* a real package. I don't think Evolution *per se*, but the *evolution-data* package is crucial to the functioning of Gnome, so I don't think you want to remove that.

In any case, if you're using any kind of decent package manager--*aptitude*, *apt-get*, or Synaptic... **not** Adept--you'll be warned of what packages are to be removed.

If only *ubuntu-desktop* is to be removed, it's fine. If you notice about twenty or fifty packages to be removed, you may not want to do that.

---

