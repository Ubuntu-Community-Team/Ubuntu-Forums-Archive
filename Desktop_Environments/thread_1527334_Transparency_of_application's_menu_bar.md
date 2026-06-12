---
title: "Transparency of application's menu bar"
date: 2010-07-09
forum: Desktop Environments
---

### Post by leseman on 2010-07-09
Hi,

I currently have a transparent desktop environment in Ubuntu 10.04. However (and I've done an extensive time searching Google), is it possible to make the application's menu bar (i.e., saying 'File', 'Edit' etc.) transparent? I'm using Compiz.

Cheers,

Jim

---

### Post by tenhi on 2010-07-09
Hi.

I have transparent menus after installing ubuntu tweak package. 
You can enable transparent menus in Desktop/Compiz settings section.

see ya.

---

### Post by mcduck on 2010-07-09
> **leseman said:**
> Hi,

I currently have a transparent desktop environment in Ubuntu 10.04. However (and I've done an extensive time searching Google), is it possible to make the application's menu bar (i.e., saying 'File', 'Edit' etc.) transparent? I'm using Compiz.

Cheers,

Jim

Sorry, but not in any easy way.

While Compiz is able to make things transparent at window level, it's not able to affect what's running inside that window, so it can't make any difference between application background and text, or different parts of the application's interface. That's something that the toolkit used to draw the application (and the application itself) must do. So it's up to GTK, Qt or whatever your application uses to allow such transparency.

The Murrine theme engine for GTK does support transparency, but as far as I know it's still not in the version that Ubuntu has. But if you install a development version of Murrine engine you will get the effect you want, at least on the programs that support it.

edit: what the poster above is talking about is making the menus themselves transparent, not the menu bar. That's something Compiz can do, since the menu is a window of it's own, not part of some larger window. Of course even in that case Compiz will make the whole menu transparent, not just the background, so you can only really use it for slight transparency effect before the menu contents become too hard to read.

---

### Post by leseman on 2010-07-09
> **mcduck said:**
> Sorry, but not in any easy way.

<...>

edit: what the poster above is talking about is making the menus themselves transparent, not the menu bar. That's something Compiz can do, since the menu is a window of it's own, not part of some larger window. Of course even in that case Compiz will make the whole menu transparent, not just the background, so you can only really use it for slight transparency effect before the menu contents become too hard to read.

Cheers, I thought it won't be possible. My 'main' menu and program menus are transparent, but that menu bar is not. So, maybe it will be possible in the future.

---

### Post by mcduck on 2010-07-09
If I remember right application transparency support is one of the goals for Ubuntu 10.10, but we'll just have to see if it makes it into final release... :)

---

