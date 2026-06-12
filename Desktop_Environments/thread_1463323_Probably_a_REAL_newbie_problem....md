---
title: "Probably a REAL newbie problem..."
date: 2010-04-26
forum: Desktop Environments
---

### Post by ThanosIsKing on 2010-04-26
For some reason there is now an icon on my desktop called "Desktop" with a little curved arrow at the top right corner, which I assume means that it's a redirect icon (link to folder). However, all of my info still shows up when I look at the properties of the icon. I feel stupid for asking this, but can I delete this without losing any of my info on my desktop?

---

### Post by cak3 on 2010-04-26
the little arrow means that is a symlink (symbolic link), and should be safe to delete. It would show all the info because a symlink is treated like a normal file/directory by the filesystem.

not sure why it would be there though...
If you want to be sure, post a screenshot, but it should be safe to delete.

---

### Post by _0R10N on 2010-04-26
You could try this. Open a console, and cd to your desktop

```
cd $HOME/Desktop
```

then run the following command:
```
ls -l grep Desktop
```
It will show you something like

```
lrwxrwxrwx 1 orion orion  20 2010-04-26 22:39 Desktop -> /home/orion/Desktop/

```

If it starts with an 'l' then, is a link, you can remove it without any risk! if it's a folder, it will start with a 'd'.

Kind regards!

_0R10N >>

---

