---
title: "Gnome workspaces rearrange windows"
date: 2019-01-14
forum: Desktop Environments
---

### Post by LiamG on 2019-01-14
In 18.04, if I place some windows in workspace below an empty workspace, the empty workspace vanishes, as if to save space.

It looks a bit like this:

```
[x]                               [x]

[ ] -> automatically becomes ->   [x]

[x]                               [ ]


--------------
[x] represents a workspace with some windows in it and [ ] represents an empty workspace.


```

How do I turn this feature off?

---

### Post by Dennis N on 2019-01-14
Gnome desktop by default only keeps one empty workspace - the last (bottom) one. If you delete all content from a workspace, that workspace is deleted as well. 
 
The alternative is to set your workspaces to be **static** rather than **dynamic**. 
You can set this using Tweaks tool:
[B]
Tweaks > Workspaces > (select) Static Workspaces[/B]  and specify the number you want.

---

### Post by LiamG on 2019-01-14
Hmm, that's frustrating. If I have to have static workspaces, then I'm thinking I might see if I can get this working instead: [https://extensions.gnome.org/extension/484/workspace-grid/](https://extensions.gnome.org/extension/484/workspace-grid/)

---

