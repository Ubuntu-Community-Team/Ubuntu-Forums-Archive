---
title: "Windows Python install messes up gnome icons"
date: 2010-03-27
forum: Desktop Environments
---

### Post by gregsmith_to on 2010-03-27
A few weeks ago I installed Python2.2.3 for Windows in my Wine (which was 1.1.38ish at the time, I think). Why? I needed to do some automated cleanup of the wine registry.

That all worked fine, but I wound up with little green snakes all over  gnome (the old 'happy snake' python icon from 2.2, not the newer blue & yellow one).

Many, many file types show in nautilus as 'Python file (no console)' but do not have a snake logo. I think this applies to all 'text' files. When opened in gedit they have the snake logo on the tab. Perversely, actual '*.py' files sometimes have snake logo in gedit, but in any case it never selects Python syntax highlighting for these (which it did before I installed WinPy). 

I realize this is probably a Wine issue (in general I do not want install of windows apps to redecorate my gnome view), but the fix I need is to remove this corruption of the desktop -- and I have no idea where Gnome implements the file-type -> icon mapping mechanism, If I knew that I could probably go in and just delete something. I've spent most of an hour looking through menus, online help, and google search results with no luck at all (I found something that applied to Gnome 1.4, though).

I could try uninstalling win-python but that's not really a solution for me (especially if it doesn't fix the problem!)

Any pointers? Thanks

(Hardy on amd64)

---

### Post by niXel on 2012-12-14
Strange. I have the same problem now.
Did you manage to fix this?

---

### Post by niXel on 2013-01-07
Hm. Could anybody tell me where I can find the edit-button?
I just see quoting- and replying-buttons but no edit!?

Anyway&#8230; there are some definitions set in

~/.local/share/mime/packages/x-wine-extension-pyw.xml

and there is something in ~/.wine/system.reg

> [Software\\Classes\\Python.NoConFile] 1353330378
@="Python File (no console)"

I just removed ~/.local/share/mime/packages/x-wine-extension-pyw.xml and hope that it will be fixed after an reboot.

Okay so removing the mime type definition logging out and in again worked.
I also executed update-mime-database before.

PS: I can edit the last reply but not the one before. Is there an expiration time until I can edit my messages?

---

