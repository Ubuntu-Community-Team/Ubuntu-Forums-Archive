---
title: "Window objects capture mouse focus"
date: 2005-03-10
forum: Desktop Environments
---

### Post by yippy on 2005-03-10
I had Gentoo last week (for two years), and after a big update world I ran into this problem (I'll describe it in a minute).  What the heck, I have Ubuntu on my laptop I might as well install it on the desktop too, so I installed Ubuntu warty, but had the same problem, I went ahead and dist-upgraded to hoary because that was my plan anyway, and the problem still exists.  Here it is:

The mouse focus gets stuck on a particular window element.  For example, if I run Synaptic and click the category list to scroll through, the mouse focus won't leave that element.  When I click anywhere on the screen, it selects an item on the list as if I had stayed within the window, if I click above the list it selects the top item, below it selects the bottom item, etc.  The only way I can get it to let go is if I close the application.  I am still able to use the keyboard to tab out, but if I click the mouse it jumps back.  It's especially irritating if I click an icon on the toolbar, because it gets stuck on that icon.  If I click anywhere else on the screen, it clicks that button again.

I installed Pekwm (because it rocks), and found that if I let gdm log me in I have the same problem, but if I stop gdm and use startx instead, it works.  Once in a while after gdm was running it will still happen in pekwm, but the problem seems to go away after a few minutes and stays gone until I restart my computer and gdm picks up again.

So I'm not sure what caused it.  I didn't use gdm in Gentoo, where I had this problem originally, so I don't think gdm is the problem.  I guess Gnome because I think at least the gnome libraries are loaded whenever it happens.  I don't think I have any special hardware, just an AthlonXP, Geforce4, standard 3-button logitech mouse.

Has anyone else run into this issue?  Or better yet, does anyone know what the heck is happening so I can maybe resolve it?  It's a *little* bit irritating.

Joejoejoe

---

