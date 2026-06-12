---
title: "KMail not working because libkmailprivate.so.4 has an undefined symbol"
date: 2009-03-06
forum: Desktop Environments
---

### Post by Virtualboxbuntu on 2009-03-06
I'm using Linux Mint 6 KDE CE RC1. KMail isn't installed by default, so I install it. When I run Kontact, I get this error message:

Cannot load part for Mail.
QLibrary::load_sys: Cannot load /usr/lib/kde4/kmailpart.so (/usr/lib/libkmailprivate.so.4: undefined symbol: _ZN4KPIM8KMeditor16contextMenuEventEP17QContextMenuEvent)

It turns out that libkmailprivate.so.4 is a link to libkmailprivate.so.4.1.0. But Linux Mint uses KDE 4.2, do I need to go somewhere to download a 4.2.0 version of this file? I'm not that experienced with KDE, I've used GNOME a lot more (I prefer KDE though).

When I click OK in the error message, Kontact loads as normal but Mail is disabled. It won't close when I click the "x" button in the top-right corner but closes when I click File>Quit.

---

### Post by Virtualboxbuntu on 2009-03-07
After some research, I think I need to download libkmailprivate.so.4.2.0 and replace libkmailprivate.so.4.1.0 with it.

I can't seem to find that file anywhere, except in the form of an RPM package that won't open or convert with alien.

---

