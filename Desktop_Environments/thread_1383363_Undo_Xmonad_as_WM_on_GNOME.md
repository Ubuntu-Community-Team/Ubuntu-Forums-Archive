---
title: "Undo Xmonad as WM on GNOME"
date: 2010-01-17
forum: Desktop Environments
---

### Post by graabein on 2010-01-17
Hi, I followed [this page]("http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome#Ubuntu_Jaunty") and did
[COLOR="Navy"]# gconftool-2 -s /desktop/gnome/session/required_components/windowmanager xmonad --type string[/COLOR]

to use Xmonad instead of Metacity on GNOME. It didn't quite work out the way I wanted it to, and I don't feel like using time adjusting GNOME to work with Xmonad, so I wonder how I can unset it to get Metacity back?

---

### Post by graabein on 2010-01-17
I took a stab at 
[COLOR="Navy"]# gconftool-2 -s /desktop/gnome/session/required_components/windowmanager **metacity** --type string[/COLOR]

and that worked just perfect. Problem solved.

---

