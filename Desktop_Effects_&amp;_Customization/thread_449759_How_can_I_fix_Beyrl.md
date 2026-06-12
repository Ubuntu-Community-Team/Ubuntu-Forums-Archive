---
title: "How can I fix Beyrl?"
date: 2007-05-20
forum: Desktop Effects &amp; Customization
---

### Post by DeadSuperHero on 2007-05-20
Right, I've had this installed and running ever since I got my nVidia card working properly.
However, the other day I installed Ubuntu Studio.
I've resolved the black screen issue by using aptitude to get rid of all the Ubuntu Studio packages, and so I'm back on Feisty, I guess.
However, Beyrl stopped working. It's still there, but it doesn't do anything. The windows are boring again!
How do I get it working again?
Also, I have a problem with GNOME sometimes. When I boot up, and log in, the panel is sometimes missing.
I have to log back out, and login again. What causes this? How can I fix it?

---

### Post by Ateo on 2007-05-21
Can you add some more detail? What part of beryl is working/not working? Does beryl launch at startup? Are you sure it's not Emerald that isn't loading?

---

### Post by DeadSuperHero on 2007-05-21
It just doesn't work at all on my account anymore.
However, when I log in as root, it works fine. Is this a permissions error for Beyrl?

---

### Post by ykpaiha on 2007-05-21
> **Mr. Psychopath said:**
> It just doesn't work at all on my account anymore.
However, when I log in as root, it works fine. Is this a permissions error for Beyrl?

-try to remove any beryl rc and-or ./beryl in your home
most probably it left some odds from previous sessions.

---

### Post by DeadSuperHero on 2007-05-21
Erm, how do I do that? I assume this would be a terminal command, but which one is it?

---

### Post by DeadSuperHero on 2007-05-23
All right, I've gotten Beyrl working again...mostly. All I did was change the Window Manager to "Beryl"
However, now I have 8 workspaces on the cube, making it an awkward octagon.
I tried changing the number of workspaces on the little workspace area, but no good.
I think it has something to do with the .beyrl file in my home folder, but I really can't do anything with it, seeing as it's hidden.
What to do?

---

### Post by medley on 2007-05-23
> **Mr. Psychopath said:**
> All right, I've gotten Beyrl working again...mostly. All I did was change the Window Manager to "Beryl"
However, now I have 8 workspaces on the cube, making it an awkward octagon.
I tried changing the number of workspaces on the little workspace area, but no good.
I think it has something to do with the .beyrl file in my home folder, but I really can't do anything with it, seeing as it's hidden.
What to do?

You don't change how sides the beryl cube has in your taskbar; you do it in beryl-settings. This should have been installed in your program menus. If not, you can run it in a terminal session. I'm not at one of my linux systems right now, so can't tell you for sure to set it (possibly 'desktop') in beryl-settings, but you should set number of desktops to 1.

---

### Post by DeadSuperHero on 2007-05-25
Well,I still get an ocatgon instead of a cube.
But it's different when I run as root...weird.
What is an easy way to just make it into a normal, four-sided cube?

---

