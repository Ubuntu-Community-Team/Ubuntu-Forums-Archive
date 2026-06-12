---
title: "Error when setting file/folder prefs"
date: 2006-03-28
forum: Desktop Environments
---

### Post by neilmusgrove on 2006-03-28
When i set file or folder permissions via rightclick->properties i always get the attatched error dialogue. The permissions do set correctly because when i reopen the dialogue, the changes have been saved, the error is really annoying though.

Anyone any ideas what might be causing it?

Cheers

Neil

PS I'm using Kubuntu with KDE 3.5.1

---

### Post by Parkotron on 2006-03-29
I can confirm this behaviour under Kubuntu Breezy with KDE 3.5.1. No idea what's causing it though. It's never worried me too much because the changes actually do take effect, and I rarely use Konqueror to change file properties.

That said, this is definately a bug. I'm planning to upgrade to 3.5.2 a bit later, so I'll check to see if this has been fixed there. I might also be fixed in Kubuntu Dapper.

Sorry, I couldn't be of more help, but at least you now know your not alone on this issue.

---

### Post by neilmusgrove on 2006-03-30
Ok,

Thanks for your help

Neil

---

### Post by Mau on 2006-03-30
If you set the permissions via the command line, it will set correctly.

For just this folder: $ chmod xxx /path/to/folder
or for all sub-folders too: $ chmod xxx /path/to/folder -R

---

### Post by neilmusgrove on 2006-03-30
Well, i've just upgraded to KDE 3.5.2 and it's fixed!

Well done KDE.

Neil

---

