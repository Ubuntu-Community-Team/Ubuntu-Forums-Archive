---
title: "Help, dont want to break beryl"
date: 2007-01-10
forum: Desktop Environments
---

### Post by Naegling23 on 2007-01-10
Ok, so I am running beryl on AIGlx.  I am getting an upgrade request for 

Linux-restricted-modules-2.6.17-10-386

I have 2.6.17.6-2~amaranth which, at least at the time was necessary for beryl to run.

The upgrade also wants to upgrade xserver-xorg-core
It also wants to remove nvidia-glx, once again, im running the amaranth version.

Please help me, it looks like upgrading will break beryl, which I obviously dont want to do.

Do I suck it up and upgrade, or do I need different repositories??

---

### Post by vlad.b on 2007-01-11
Are you using Beryl SVN? Personally I'd slap in the svn repositories and upgrade what I would need to. But keep in mind I don't have anything on my computer worth keeping at the moment. To my understanding, X.Org supports GLX now and the separate glx driver wouldn't need to be installed. (I know I didn't need to install it) Here I can honestly say I don't have much knowledge, but feel free to experiment a little bit if you can afford it. 


Here is the guide that I used. The server seems to be down for the moment, but it should be back up. <a href="http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft">Beryl How-To</a>

P.S. I installed it with a 6600 nvidia card.

Good luck

---

