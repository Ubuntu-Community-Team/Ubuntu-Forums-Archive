---
title: "Go back to default search tool?"
date: 2007-11-05
forum: Desktop Environments
---

### Post by deerfieldtech on 2007-11-05
I've removed tracker as I prefer the default GNOME search tool (whatever it is) that is in Feisty. Unfortunately, removing tracker doesn't seem to restore anything, I'm just left with no search capability in nautilus. I also get this error after attempting a search:

```
The folder contents could not be displayed.
The name org.freedesktop.Tracker was not provided by any service files
```

Just wondering how to restore the old search tool in GNOME and do away with tracker.

Thanks in advance,

-P

---

### Post by Jussi Kukkonen on 2007-11-05
install package *beagle*

---

### Post by deerfieldtech on 2007-11-05
Hi Jussi;

Thanks for the reply, but another index based search tool that sucks up all kinds of processing power isn't what I want, I want (I've figured this out since my last post) gnome-search-tool to function as it does in Feisty. It is installed by default in the gnome-utils package in Gutsy, but for some reason is not automatically restored when tracker is removed.

-P

---

### Post by Jussi Kukkonen on 2007-11-05
oh, ok.

gnome-utils has no relation to tracker, has it? I don't think gnome-utils has been automatically removed either, it should be there... If it isn't, there should be nothing stopping you from installing it.

Or did I somehow misunderstand what you mean by "automatically restored"?

---

### Post by deerfieldtech on 2007-11-05
> **Jussi Kukkonen said:**
> oh, ok.

gnome-utils has no relation to tracker, has it? I don't think gnome-utils has been automatically removed either, it should be there... If it isn't, there should be nothing stopping you from installing it.

Or did I somehow misunderstand what you mean by "automatically restored"?

Jussi;

gnome-utils is not related to tracker. gnome-search-tool, which is what runs when you select "Search for Files..." in the Places menu on the gnome desktop, is in the gnome-utils package. And yes, gnome-utils is installed. My hope was that uninstalling tracker would restore gnome-search-tool as the search tool, but no luck there. I found a bug report at bugzilla.gnome.org (which of course I can't find now) that suggested that tracker was hardcoded into nautilus (or at least, calling tracker's lib was hardcoded into nautilus). Removing it therefore leaves nautilus without a search tool, which is what causes the error I'm seeing.

If I recall correctly this bug report also said that Fedora was using a patch to get around this issue, and in fact F8 just uses gnome-search-tool in nautilus by default.

-P

---

### Post by dj_flx on 2008-02-01
So how do we go about getting this bug fixed?

I see this has been at least since November, is anything forthcoming?

I don't have a lot of processor or disk space to squander, so this really hurts me.

-Michael

---

