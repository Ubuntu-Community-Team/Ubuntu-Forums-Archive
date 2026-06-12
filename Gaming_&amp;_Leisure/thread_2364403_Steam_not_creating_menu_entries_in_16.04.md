---
title: "Steam not creating menu entries in 16.04"
date: 2017-06-22
forum: Gaming &amp; Leisure
---

### Post by CatKiller on 2017-06-22
I've recently upgraded from 14.04 to 16.04. Steam is no longer creating menu entries for newly-installed games like it used to.

It downloads the icons for the menu entries, but doesn't actually create the .desktop files in ~/.local/share/applications as it did previously. When selecting "create Desktop shortcut" from the context menu within the Steam client, it fails.

Has anyone else seen this? And hopefully fixed it?

---

### Post by Perfect Storm on 2017-06-23
No problems here with 16.04 and steam (clean install). Is the permission set correctly in ~/.local/share/applications ?

---

### Post by CatKiller on 2017-06-23
Thanks for the reply. Certainly I was able to create files in there (I created the .desktop files myself when Steam hadn't). Out of interest, what are the permissions set to on your ~/.local/share/applications?

Looking at the difference between ~/.local/share/applications and ~/.local/share/icons (where Steam has been able to create files) icons has "Access files" for Group and Others, whereas applications doesn't. I'm not sure that that would make a difference, but I'll change it to be the same to see if it helps.

Weird if permissions get changed on an upgrade, though.

---

### Post by Perfect Storm on 2017-06-23
My permission is:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=275739&stc=1&d=1498222588[/IMG]

---

### Post by CatKiller on 2017-06-23
So, the same as I had. Giving permissions to Group and Everyone didn't help, either.

---

### Post by Perfect Storm on 2017-06-23
What about verifying game cache?

I read someone solved it by launching steam as admin. But that is not advisable.

Does steam comes with some output when trying making shortcut?

---

### Post by CatKiller on 2017-06-23
It says > Could not create shortcut.
A shortcut to this game is probably already on the desktop.

Permissions problems would prevent it from writing, so it seems a likely avenue. Not sure how best to approach it though.

When installing the game it gives no errors.

---

### Post by Perfect Storm on 2017-06-23
There's a bug report on this, hopefully they fix it soon: [https://github.com/ValveSoftware/steam-for-linux/issues/5012](https://github.com/ValveSoftware/steam-for-linux/issues/5012)

---

### Post by CatKiller on 2017-06-23
Ah, good spot, thank you!

Hopefully they'll do a fix. I'll just keep making shortcuts manually till then, in that case. I'm used to tweaking them to make them use the freedesktop.org game categories.

The biggest chunk of game installs I'm planning on doing in the future will be for my HTPC when I've built it, but that will be using Big Picture Mode, so this bug won't be an issue.

Thank you again for tracking down the bug report.

---

### Post by Perfect Storm on 2017-06-23
I've just downloaded a game through steam, and I now experiencing the same problem.

---

### Post by CatKiller on 2017-06-26
> **Artificial Intelligence said:**
> I've just downloaded a game through steam, and I now experiencing the same problem.

Sorry to hear that. I hope they fix it quickly for you, too.

---

### Post by CatKiller on 2017-06-26
For anyone else that has the same problem, I've written a [little howto]("https://ubuntuforums.org/showthread.php?t=2364670") for how to create launchers by hand.

---

