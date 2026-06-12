---
title: "How to diasble the shortcut &quot;alt+left click&quot;?"
date: 2008-12-16
forum: General Help
---

### Post by Hrvig on 2008-12-16
Hello,
As the title says, I want to disable the shortcut.
I've tried system -> settings -> keyboard shortcuts - but it is not there.
Does anyone have an idea where to go?

My problem is that Adobe Photoshop 7.0 which I run under Wine uses this short-cut, and the feature is not available unless I can use "alt+ left click".

Any help would be appreciated.
Greetings from,
Jakob

---

### Post by darkknight045 on 2008-12-16
Actually what you need is found in Compiz, I believe there should be a window options section in there.  In that section should be a move window hot key and you can adjust it to whatever you want. (I use Super+left click).

I wish I could be more specific but I don't have my Ubuntu PC in front of me.

If you don't have it already use this to install the Compiz manager:

```
sudo apt-get install gnome-compiz-manager
```

This will give you a GUI to make adjustments to your compiz settings.

---

### Post by ajcham on 2008-12-16
Almost right DarkKnight, but it is not a Compiz feature - I run metacity and have the same function available.

System > Preferences > Windows

You can't disable, but you can change the key binding to control or super.

---

### Post by darkknight045 on 2008-12-16
> **ajcham said:**
> Almost right DarkKnight, but it is not a Compiz feature - I run metacity and have the same function available.

System > Preferences > Windows

You can't disable, but you can change the key binding to control or super.

Hmm..

Perhaps Compiz just has a redundant menu to control that then.

---

### Post by Hrvig on 2008-12-16
Thanks!
The Compiz thing worked, but it is changeable the other way aswell :)
Finally I can use the repair-tool in Photoshop!

---

### Post by ajcham on 2008-12-16
> Hmm..

Perhaps Compiz just has a redundant menu to control that then.

Ahh, so it does.  I did check before, but the Compiz option appears under Uncategorised, rather than Window Management where I would have expected.

---

