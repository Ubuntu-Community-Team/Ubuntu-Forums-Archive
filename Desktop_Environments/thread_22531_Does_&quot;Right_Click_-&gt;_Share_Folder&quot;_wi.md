---
title: "Does &quot;Right Click -&gt; Share Folder&quot; with samba work."
date: 2005-03-28
forum: Desktop Environments
---

### Post by panabar on 2005-03-28
What should I do to easily share folders using right-click "share folder" with samba?

I can't seem to share folders using gnome-shared-folders application, but sharing folders by fallowing ubuntu starter guide works flawlessly.

Is it gnome-shared-folder application or should I check something that should be enabled by default, but is not?

When I share folders with this right-click share folder or system-administration-shared folders remote computers (on my network) say that my computer refuses connections.

Thank You

---

### Post by glens on 2005-03-29
Here's what I did.

Right clicked to share a folder.  Entered the details in the dialog.  Then tried to browse the share from windows.  No luck.  It didn't authenticate at all.

Then I read something about running smbpasswd to set up an smb password.  Tried that can it worked but instead of having just the folder I asked to share I noticed it's sharing the home folder too!

Is it really supposed to work like this???  It should be straightforward but this just doesn't seem to work in any sane way.

---

### Post by Nebvin on 2005-03-30
samba is set up to show the home folders by default

---

### Post by gstamp on 2005-03-30
[QUOTE=Nebvin]samba is set up to show the home folders by default[/QUOTE]

Seems like a bad idea... you don't see it as being shared in under the shared folders dialog either.  Seems like the whole integration with the GUI needs work.

---

