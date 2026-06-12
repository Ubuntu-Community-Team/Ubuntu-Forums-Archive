---
title: "How can I open Wine applications maximized?"
date: 2005-11-13
forum: Desktop Environments
---

### Post by aysiu on 2005-11-13
So all of my regular Linux apps (KDE and Gnome ones) remember the last size the app was (or at least they all open maximized, which is what I like), but I use Filezilla under Wine, and it never seems to open maximized. Is there something I can append to the *Wine* command to make the window open maximized? I can press Alt-F10, but should I have to do that every time? I've already tried poking around *man wine*, but I couldn't find anything on an "open maximized" option.

---

### Post by Remmelas on 2005-11-13
some windows apps have 'maximize' arguments available to them.  For example, if i remember correctly, for internet explorer, you could do wine iexplore /maximized to open ie maximized(i used to do web site development, so had to have ie in linux)

---

### Post by aysiu on 2005-11-13
Thanks for the suggestion. Unfortunately, if I add */maximized* to the Wine Filezilla command, it tries to FTP to /maximized.

---

### Post by Zotova on 2005-11-13
I may be wrong but isn't it -maximize or just -m?

For example 'wine /.../filezilla.exe -m'

Also, out of interest you said all your gnome and kde apps start full screen. Do you use amarok by any chance? As that little pest starts in random sizes for me.

---

### Post by aysiu on 2005-11-13
[QUOTE=Zotova]I may be wrong but isn't it -maximize or just -m?

For example 'wine /.../filezilla.exe -m'[/quote] Thanks for the suggestion. Unfortunately neither of those works.

> 
Also, out of interest you said all your gnome and kde apps start full screen. Do you use amarok by any chance? As that little pest starts in random sizes for me. No. I use JuK. Sorry.

---

### Post by aysiu on 2006-08-25
Bump...?

---

