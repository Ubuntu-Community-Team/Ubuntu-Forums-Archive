---
title: "Strange upper panel for second user."
date: 2010-03-17
forum: Desktop Environments
---

### Post by ConDsenXieN on 2010-03-17
I'm having a slight issue with Xubuntu Karmic right now and am going nuts trying to figure it out.

My environment works just fine, I have my upper panel, Applications and Places on the left hand side, clock, sound, network, battery etc on the right.

My wife's login on the other hand, lately her panel has started going haywire. Her lower panel is fine(workspace switch, etc). Her upper however, as of two days ago, seems to be pretty messed up. Her Applications and Places menus disappeared into thin air, no matter what I tried to do to fix the issue. She now has Apps and Places on the RIGHT as opposed to the left(strange), the Firefox and Help launchers on the right, and seemingly no way to get them to move no matter what I do.

We use Compiz Fusion but I don't think it would be affecting this. I've tried to remake the panel with the same results. :X Any ideas?

---

### Post by denham2010 on 2010-03-18
> **ConDsenXieN said:**
> We use Compiz Fusion but I don't think it would be affecting this. I've tried to remake the panel with the same results. :X Any ideas?

By 'remake the panel' do you mean you just delete all the applets and re-add them, or do you completely delete the panel and start it from scratch?

From the sounds of it, you might have a spacer on the panel, and the applets have been moved to the right of the spacer.

Alternatively, you can open the following file in mousepad:

```
~/.config/xfce4/panel/panels.xml
```

This is an easy to read xml file describing your panels layout. You should be able to move things around manually in here, save, and log out to effect the changes (obviously, make a back-up copy of the original file incase any changes corrupt the file).

By looking at this file, you may find the culprit that is messing up the
 panel.

Cheers.

---

### Post by ConDsenXieN on 2010-03-18
Thank you!

I'll definitely look into it.

And by "remake the panel", I mean I deleted it and remade it with the applets and such.

I'll definitely log in to her side of X later on tonight and see what's causing the odd spacing issue. It doesn't look like I jacked anything up in there, but you never know...:X

Cheers, mate. :D

---

