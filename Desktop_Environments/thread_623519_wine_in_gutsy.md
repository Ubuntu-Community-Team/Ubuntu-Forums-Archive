---
title: "wine in gutsy"
date: 2007-11-25
forum: Desktop Environments
---

### Post by mosaic2s on 2007-11-25
when i click on configure wine from applications menu - the system hangs. many times it has happened.

any advice?

---

### Post by hotweiss on 2007-11-26
If you are after games, I'd suggest you try Cedega... works like a charm.

---

### Post by sojusnik on 2007-12-03
Where is the difference between Wine and Cedega?

What runs smoother with Civilization 4?

---

### Post by apienk01 on 2007-12-16
> **mosaic2s said:**
> when i click on configure wine from applications menu - the system hangs. many times it has happened.

any advice?

Type 'winecfg' in terminal. If the system hangs again, you have a problem with wine. Try reinstalling from [WineHQ]("http://www.winehq.org/site/download-deb") repository if you are not using it already. The version on Gutsy official repositories is 0.9.46 while on WineHQ there are updated packages. The current one is 0.9.51. Many bugs have been fixed.

> **sojusnik said:**
> Where is the difference between Wine and Cedega?

What runs smoother with Civilization 4?

Cedega is a commercial fork of Wine. It has numerous enhancements which allow games to run, or just to run better. It also features a versatile installer for Windows games. But the main real difference between Cedega and Wine used to be the support for various CD checks like Safedisc which is needed to run most recent games, at least from original CDs. It used to be, but it isn't anymore. Safedisc support have just been added to Wine, and many games work just great with original CDs. So try Wine first, and buy Cedega only if your game doesn't work in Wine and is listed as supported on Cedega's website. Beware though that even Cedega won't let you play multiplayer games on servers protected by Punkbuster. Punkbuster is so tightly connected with Windows that it is not possible to implement on a simple compatibility layer like Wine or Cedega. The only way out is to use double boot system or vmware, but for these you have to own Windows.

Civilization works with some minor graphics problems in Wine according to [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4036&iTestingId=2775") WineHQ page. My bet is that Cedega runs it a little bit better.

---

