---
title: "App to find mediacode of discs?"
date: 2005-12-15
forum: General Help
---

### Post by helwitch on 2005-12-15
I've got a NEC 3500AG DVDRW drive, and I bought a bunch of memorex 16x DVD-Rs. K3B won't burn to these discs. it says to try discs recommended by the manufacturer. Is there an app that will let me find the mediacode of the discs, or a way to find the media code without an app, so I can see they are supported by any third party firmware, and see why on earth memorex discs wouldn't work?

---

### Post by nocturn on 2005-12-15
[QUOTE=helwitch]I've got a NEC 3500AG DVDRW drive, and I bought a bunch of memorex 16x DVD-Rs. K3B won't burn to these discs. it says to try discs recommended by the manufacturer. Is there an app that will let me find the mediacode of the discs, or a way to find the media code without an app, so I can see they are supported by any third party firmware, and see why on earth memorex discs wouldn't work?[/QUOTE]

cdrecord can do that.

---

### Post by helwitch on 2005-12-15
which command?

---

### Post by nocturn on 2005-12-15
[QUOTE=helwitch]which command?[/QUOTE]

I'm not sure, but check the cdrecord man page.

If you do a dummy burn with the verbose option it should show it in any case.

---

### Post by helwitch on 2005-12-15
I'd looked through the list of commands, but hadn't checked the man page. I'll do so. And try the verbose dummy burn if I can't figure it out otherwise. thanks!

---

### Post by alcachi on 2007-01-17
The following commands can be used:
cdrdao disk-info
cdrecord -atip

PS. Just in case you hit this page through a google search ;-)

---

