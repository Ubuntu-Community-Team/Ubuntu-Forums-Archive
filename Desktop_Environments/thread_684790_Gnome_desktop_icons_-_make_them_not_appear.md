---
title: "Gnome desktop icons - make them not appear?"
date: 2008-02-01
forum: Desktop Environments
---

### Post by myke on 2008-02-01
Can I set up Gnome where the desktop icons such as my portable drives that automount do not appear on the desktop?  I'd rather just have a panel launcher.  Also, my WD Passport portable hard drive when mounted under Gnome always shows up with 2 icons and it is not partitioned.  When I 'safely remove' the drive while the laptop is still on, one icon will remain all by it's lonesome and resists all efforts to remove it.

I'm having so much problems with Kubuntu/KDE that if I stay with Ubuntu, I'm gonna likely need to move over to Gnome.  I was just wondering, though, how to keep my desktop free of icons.  I usually put a panel icon even for my portable drives up in KDE and would like to do the same in Gnome.

Is this possible?

---

### Post by Tenken on 2008-02-01
To stop your drive from appearing on the Gnome desktop hit Alt-F2 and type

```
gconf-editor
```

Navigate to apps->nautilus->desktop and uncheck the volumes_visible checkbox.

---

### Post by LeDechaine on 2008-02-01
Nice! I was searching for this too.

Thanks! :)

---

