---
title: "Razor-qt / openbox 11.10 system from minimal cd?"
date: 2011-12-31
forum: Desktop Environments
---

### Post by casbahdk on 2011-12-31
Does anyone have any thoughts on installing a razor-qt / openbox based system from a minimal cd? I want to avoid as many KDE and GNOME bits as possible, but I want to use terminator, and I need to be able to use usb-modeswitch, so I guess wicd is ruled out for networking. I also need a replacement for gedit, that has most of the same features, including auto spell checking (11.04 or earlier, no auto spell check in ll.10). Kate could be a possibility, but I am not sure how many dependencies it would drag in. Lastly, I need for the mounting of USB storage devices to work out of the box. This is often an issue when installing from a minimal cd.

---

### Post by sanderd17 on 2011-12-31
> **casbahdk said:**
> Does anyone have any thoughts on installing a razor-qt / openbox based system from a minimal cd? I want to avoid as many KDE and GNOME bits as possible, but I want to use terminator, and I need to be able to use usb-modeswitch, so I guess wicd is ruled out for networking. I also need a replacement for gedit, that has most of the same features, including auto spell checking (11.04 or earlier, no auto spell check in ll.10). Kate could be a possibility, but I am not sure how many dependencies it would drag in. Lastly, I need for the mounting of USB storage devices to work out of the box. This is often an issue when installing from a minimal cd.

I have never worked with the minimal CD (but I did work with Arch, which is more minimal than Ubuntu minimal). But I can think of the following:

[LIST]
[*]you need a display manager. I guess GDM or KDM will pull a lot of dependencies you don't want, so you could try with lightDM
[*]You don't want to use KDE apps (such as Kate or Okular), as they will also ask a lot of dependencies
[/LIST]

For pure QT apps, check out this thread: [http://forum.pinguyos.com/Thread-Razor-Qt-A-New-Qt-Based-Desktop-Environment](http://forum.pinguyos.com/Thread-Razor-Qt-A-New-Qt-Based-Desktop-Environment)

---

### Post by casbahdk on 2011-12-31
Thanks for the reply and the link. I'll try to stay away from the KDE apps. Happy New Year :D

---

### Post by ratcheer on 2011-12-31
I don't know much about your specific app requirements, but Archbang uses OpenBox with the slim login manager for a very slim (pun intended) installation. I wonder what Crunchbang uses? I am guessing it is fairly similar.

Tim

---

### Post by casbahdk on 2011-12-31
> **ratcheer said:**
> I don't know much about your specific app requirements, but Archbang uses OpenBox with the slim login manager for a very slim (pun intended) installation. I wonder what Crunchbang uses? I am guessing it is fairly similar.

Tim

Cheers. According to [corenominal]("http://corenominal.org/2011/11/"), he has switched from GDM to Slim, with the latest Statler images.

---

### Post by casbahdk on 2012-01-03
I stumbled across this today, for anyone that is interested:

[Ubuntu Razor-qt Remix]("http://www.u-r-r.info/")

---

