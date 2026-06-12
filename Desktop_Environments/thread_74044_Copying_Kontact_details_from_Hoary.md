---
title: "Copying Kontact details from Hoary"
date: 2005-10-10
forum: Desktop Environments
---

### Post by thumper on 2005-10-10
I now have Breezy (this time with a separate home partition) installed on one partition with Hoary still on another.

I have booted back into Hoary while I figure out what to do next.

I need to copy all my Kontact details across, mails, contacts, settings.

I tried to copy everything from ~/.kde/share/apps/kmail and kaddressbook but that didn't work.  None of the contacts were there.  Mail was but none of the mail settings.

What am I missing?

---

### Post by aysiu on 2005-10-10
All of your personal settings live in your /home folder. Most of them are hidden files. For example, all your Firefox preferences, bookmarks, and extensions live in /home/username/.mozilla

Go to your home folder (/home/username) and click from the menu to "show hidden files."

---

### Post by claydoh on 2005-10-11
Also look in your ~/.kde/share/config dir for kmailrc and other config files

---

### Post by thumper on 2005-10-11
Yep, the ~/.kde/share/config was the bits that I was missing.

I was also temporarily confused as to why the apps/kaddressbook was not populating my kontact addresses until a quick google pointed out that it is now apps/kabc.

Also copied over ~/.mozilla/firefox and now have weather back and all my bookmarks.

I happy Breezy camper now 8)

---

