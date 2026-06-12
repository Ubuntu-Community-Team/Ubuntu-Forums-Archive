---
title: "Opening KMenu spins up NAS"
date: 2011-05-30
forum: Desktop Environments
---

### Post by MadEgg on 2011-05-30
I have a NAS in my home network which is automatically mounted using NFS on my desktop. There's only media files and documents on the NAS, no installed programs. None of those documents or media files appear in the Recently Used tab.

Whenever I click on the K-menu button of the taskbar, the menu does open but I cannot use it for a while; then I hear the harddisks in the NAS spin up and after a couple of seconds I can use the menu.

This is, of course, really annoying because it limits the speed at which I can use the K-menu. Why does it need access to the NAS anyway? Is there any way I can disable this?

---

### Post by Zorael on 2011-05-30
Do you have any of the NAS shares mounted and added to your Places list? If so, does this happen if they're unmounted or with those entries removed?

Without looking at the source I'd *imagine* that the menu is asking around for Places (and recent documents etc) to display in the Computer tab, and at that point it polls the NAS shares to see if they're still there. If the NAS doesn't have a cached response I guess it needs to spin up. And if the menu doesn't do this in a separate thread, it would lock up the rest of the menu, yes.

Do you have terminal-level access to the NAS so you can see with what options its disks are being mounted?

The KDE bug tracker is [here](https://bugs.kde.org/) if you'd like to report this as a bug.

---

### Post by MadEgg on 2011-05-31
Nope, there are no entries on any of the mounted NFS shares on the NAs in my places list. Nothing non-default at all, just Home Folder, Remote, Root, Trash and Bluetooth.

The NAS is a Netgear ReadyNAS DUO. I believe I should be able to log in using SSH but I have to find out how to enable it. I'll try. But still, I don't even think that the K-menu has any good reason to scan the NAS without any mentioning of it in the menu.

---

### Post by Zorael on 2011-05-31
Agreed.

I think this warrants [a bug report](https://bugs.kde.org).

---

