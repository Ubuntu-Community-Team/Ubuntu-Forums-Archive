---
title: "How to enable gtk file dialogs in emacs on fluxbox"
date: 2009-02-04
forum: General Help
---

### Post by phillies on 2009-02-04
Hi,

I have a problem with emacs and fluxbox running on ubuntu 8.10.
When I click on "File->Open File" I want to have the GTK file selection dialog which worked fine when I use Gnome as WM, but does not work with fluxbox even if other applications (Firefox, gedit, ...) use this dialog with fluxbox.
I googled and found:
```
(setq use-file-dialog t)
(setq use-dialog-box t)
```
but setting those variables to t, nil, 1, ... didn't have any influence on emacs.

Any ideas?

---

### Post by phillies on 2009-02-05
ok, I found a way around. emacs22-x was set as alternative which seemed to work fine with gnome but not fluxbox. Set emacs22-gtk as alternative and now I get a file open window.

---

