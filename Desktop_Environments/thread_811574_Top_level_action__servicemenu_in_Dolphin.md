---
title: "Top level action / servicemenu in Dolphin"
date: 2008-05-29
forum: Desktop Environments
---

### Post by jambalaya on 2008-05-29
Hi. I looked in google but didn't find the answer. I created a servicemenu:
[FONT="Courier New"][Desktop Entry]
ServiceTypes=all/allfiles
Actions=openWithKate
X-KDE-Priority=TopLevel

[Desktop Action openWithKate]
Name=Open with Kate
Icon=kate
Exec=kate %F[/FONT]

and copied it to /usr/share/apps/d3lphin/servicemenus and /usr/share/apps/konqueror/servicemenus.

Now, on desktop files (which is Konqueror) it works fine, the action is top-level, right under the Actions submenu, but in Dolphin, it is still within the Actions submenu. Is it possible to make it top-level in Dolphin?

Apart from that, the servicemenus for both of these apps look exactly the same, so is there a single directory for actions for both of them? Now I copy my actions to both locations, so I actually preserve two copies of the same file. This is not a big issue when it comes to storage accupation, but can be a burden when creating more and more actions, to synchronize these two dirs. I can create a symlink probably, but is there a single dedicated dir within KDE to support that?
Thanks.

---

