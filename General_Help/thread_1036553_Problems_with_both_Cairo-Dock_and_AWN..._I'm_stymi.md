---
title: "Problems with both Cairo-Dock and AWN... I'm stymied!"
date: 2009-01-10
forum: General Help
---

### Post by slinkey1981 on 2009-01-10
So I installed Cairo-Dock, because it's what I am used to. Well, what I was used to I guess. Now I can't get it to do the 3D look, the only themes it lists are _default_ and I don't know what I am doing wrong.

On initial loading after install, it lists multiple other themes, but after adding and launcher, it reverts to the flat panel look.

I'm stumped.

I've tried AWN, which I'm not a big fan of. People say you can just create a launcher and drag it onto the dock, but that hasn't worked for me, and I have never gotten a launcher to work with that dock at all.

I use a gnome-panel, and don't really want my dock to try and be my main panel, I just want it to house my application launchers.

As it is, neither of these docks are doing that for me. I know that cairo-dock CAN do it, because it has in the past.

Can someone please explain to me how to completely remove/uninstall/purge both of these docks from my system, so that I can try it over again, and which version of cairo dock to install for actual functionality?

I am using Intrepid, 32-bit. It's all updated...

---

### Post by tuxxy on 2009-01-10
If you installed from the repos then open Synaptic and search for AWN and the other deock app and remove them.  Then if they had any dependant files you may want to clean them up with an autoremove

```
sudo apt-get autoremove
```

---

