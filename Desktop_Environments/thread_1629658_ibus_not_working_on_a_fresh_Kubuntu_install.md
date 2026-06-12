---
title: "ibus not working on a fresh Kubuntu install"
date: 2010-11-24
forum: Desktop Environments
---

### Post by Dempf on 2010-11-24
I just did a fresh install from the Kubuntu DVD with my language (locale?) set to Chinese (Taiwan). However, I'm now almost completely unable to type in Chinese.

After booting into KDE, ibus-daemon appeared to be running, but there was no icon in the system tray, and no response from ibus. When I went into the Keyboard Input Menu under Applications>Settings I found that no input method was selected by default. After choosing Chewing (&#26032;&#37239;&#38899;) I can *kind of* type Chinese, but no character selection window pops up (which makes Chewing unusable).

I tried changing from ibus to ibus-kde under System Settings > Langages > System Language but it had no effect.

If I kill ibus-daemon and start it from the terminal, I  get *two* ibus icons in the system tray (and a random flashing icon in the programs list), but still no character selection window.

Does anyone have any ideas about what to do?

---

### Post by acid303 on 2010-11-24
try to install ibus from ppa
```
sudo add-apt-repository ppa:ibus-dev/ibus-1.3-maverick
```

---

### Post by Dempf on 2010-11-24
I just installed ibus from that repository and nothing has changed. The repository's site says that it's depreciated. Should I try the other one it links to?

[https://launchpad.net/~ibus-dev/+archive/ibus-1.3-maverick](https://launchpad.net/~ibus-dev/+archive/ibus-1.3-maverick)

Edit: I just tried running "ibus-daemon -x -r -d" and now ibus (and Chewing) seem to be working perfectly. Thanks a lot!

---

### Post by SnappyU on 2012-02-10
> **Dempf said:**
> I just installed ibus from that repository and nothing has changed. The repository's site says that it's depreciated. Should I try the other one it links to?

[https://launchpad.net/~ibus-dev/+archive/ibus-1.3-maverick](https://launchpad.net/~ibus-dev/+archive/ibus-1.3-maverick)

Edit: I just tried running "ibus-daemon -x -r -d" and now ibus (and Chewing) seem to be working perfectly. Thanks a lot!


Thanks!  The line "ibus-daemon -x -r -d" fixed it consistently!

---

