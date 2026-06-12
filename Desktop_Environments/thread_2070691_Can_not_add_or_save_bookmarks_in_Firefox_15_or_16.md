---
title: "Can not add or save bookmarks in Firefox 15 or 16"
date: 2012-10-13
forum: Desktop Environments
---

### Post by beyercj on 2012-10-13
I run Ubuntu 10.04 on a Desktop with Avira Antivir and could use Firefox 3.x for years without problems. Since upgrading to Firefox 15.0.1 and 16.0.1 via Synaptic the message "The bookmarks and history system will not be functional because one of Firefox's files is in use by another application.Some security software can cause this problem." I tried
- to start Firefox in safe mode disabling extensions (Noscript, Ghostery, Places maintenance (hangs at executing tasks...), Ubuntufox as well as stopping the virus scanner AVGuard)
- replacing sqlite.places
- resetting firefox to factory defaults

I note the lock file in the firefox profile which appears after starting and disappears after topping firefox but the link is broken. I tried to delete it but it renews itself.

All to no avail. Any other ideas or is it time to change to Epiphany or Chromium?

---

### Post by ajgreeny on 2012-10-13
I am also running 10.04 with FF 16.0.1 and have no problem adding bookmarks.

Try renaming the **~/.mozilla** folder in your home and then restart FF.  If you can now add bookmarks easily it is your profile that is corrupt and at fault.

You can just start again with that new profile, though you will have to get all your add-ons again, but you will be able to retrieve your old bookmarks from the old renamed **~/.mozilla/firefox/x#x#x#x#x#.default/bookmarkbackups** folder, along with other folders but do it one by one or you may end up where you started, unable to add bookmarks again.

---

### Post by beyercj on 2012-10-14
Thanks for your quick reply. I renamed the .mozilla profile folder before starting Firefox. Firefox does not show the message but I still can not add bookmarks. The new .mozilla profile folder also shows a places.sqlite.corrupt file in addition to places.sqlite.

Any more ideas?

---

### Post by ajgreeny on 2012-10-14
Sorry, but apart from removing that new ~/.mozilla folder with the corrupt places.sqlite.corrupt file in it, then purging FF and reinstalling it, I can't think of anything else.

A new profile usually sorts out these problems but it seems there is more at fault with yours than just that.

---

### Post by Insomn1a on 2012-10-14
Try running sudo firefox from terminal and see what you can get.

it could be a permissions problem.

---

### Post by ajgreeny on 2012-10-14
> **Insomn1a said:**
> Try running sudo firefox from terminal and see what you can get.

it could be a permissions problem.
That is not really a solution as it is never a good idea to run any application that has access to the internet with root permissions. Therefore you can not safely use FF that way for general browsing.  If you choose to do so to check out the problem, do not leave FF running any longer than necessary.

---

