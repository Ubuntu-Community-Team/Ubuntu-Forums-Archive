---
title: "Nautilus shows unwanted locations"
date: 2012-01-24
forum: Desktop Environments
---

### Post by ChrisOfBristol on 2012-01-24
(Ubuntu 11.10) with Gnome fallback (ie no Unity)

Nautilus shows a bookmark to Desktop which I don't want. It is under Computer rather than Bookmarks. I think I probably created it (as a bookmark) when I first started using this setup as the Desktop didn't show files. Not removable by right-clicking as Remove is greyed-out or by Menu /Bookmarks/Edit Bookmarks as it doesn't appear.
There is no Downloads under Computer - is that relevant? I think I changed my preferred destination for downloads to Desktop at some point - but that can only be done in a browser can't it?

---

### Post by ChrisOfBristol on 2012-02-04
I've now found a way of avoiding this problem.

---

### Post by sparhawkthesecond on 2012-05-18
Can you describe your method of avoiding the problem?

---

### Post by sparhawkthesecond on 2012-06-21
ChrisOfBristol, could you please explain how you customised the "Computer" section of the sidebar?

---

### Post by markbl on 2012-06-21
> **sparhawkthesecond said:**
> ChrisOfBristol, could you please explain how you customised the "Computer" section of the sidebar?
What kind of poster is he to come back here and announce he has found a solution, and yet not offer any hint to it!? :???:

Anyhow, he was complaining about the Desktop shortcut under the Computer group in the Nautilus pane. You will notice that this shortcut only appears if you "have file manager manage the desktop" enabled in gnome-tweak-tool.

The "gnome 3 way" is to leave this disabled. Now I am used to it, I realise there really was/is no need for any "special" handling of the Desktop folder by the DE (and that goes for Trash etc as well).

---

### Post by sparhawkthesecond on 2012-06-22
> **markbl said:**
> What kind of poster is he to come back here and announce he has found a solution, and yet not offer any hint to it!? :???:
Haha, yes. So frustrating!
> **markbl said:**
> 
Anyhow, he was complaining about the Desktop shortcut under the Computer group in the Nautilus pane. You will notice that this shortcut only appears if you "have file manager manage the desktop" enabled in gnome-tweak-tool.

Just to be clear that we're talking about the same thing, I'm talking about the issue as reported [here]("http://askubuntu.com/questions/79150/how-do-i-remove-some-of-my-home-folders-from-the-nautilus-sidebar"). I've not installed gnome-tweak-tool, so I'm not sure that my issue is related to that (although I've fiddled with dconf a bit). And the comments in the link suggest that everyone has this issue from a vanilla Ubuntu install. I'm not 100% sure, but (from googling) isn't that gnome-tweak-tool option to do with the desktop itself, rather than the natuilus windows?

---

### Post by markbl on 2012-06-22
> **sparhawkthesecond said:**
> I've not installed gnome-tweak-tool, so I'm not sure that my issue is related to that (although I've fiddled with dconf a bit).
Forget about gnome-tweak-tool specifically. I am just pointing out that if you have the nautilus manage the desktop then the Desktop shortcut will appear, if you don't have that enabled then it won't appear. There are probably heaps of ways to enable the "file manager manage the desktop" toggle option. I know of gnome-tweak-tool but probably all the various ubuntu-tweak tools, gconf/gsettings/dconf, etc tools can do it. I can't remember whether that setting is enabled in a clean default install of ubuntu.

---

### Post by sparhawkthesecond on 2012-06-22
Ah ok... I've got it now. I was thinking more about general personalisation of what goes into the sidebar shortcuts (as per the linked thread). I installed gnome-tweak-tool to see what the effects of turning off "file manager manage the desktop" are, and indeed, the "desktop" icon disappears. I was thinking about full customisation of the items in this sidebar, but I guess this is indeed not customisable.

Thanks for your comments and clarification.

---

