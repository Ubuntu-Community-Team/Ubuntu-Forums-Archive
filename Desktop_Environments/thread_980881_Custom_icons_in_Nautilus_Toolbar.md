---
title: "Custom icons in Nautilus Toolbar"
date: 2008-11-13
forum: Desktop Environments
---

### Post by castawaybcn on 2008-11-13
Hi there,
I have been playing with the look of my desktop for a while and I found you can customise which buttons show on your nautilus toolbar by editing:
```
/usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
```

Other than the default buttons I found you can add these:
```

<toolitem name="Cut" action="Cut"/>
<toolitem name="Copy" action="Copy"/>
<toolitem name="Paste" action="Paste"/>
<toolitem name="Trash" action="Trash"/>
<toolitem name="New Folder" action="New Folder"/>

```

Is that all there is? Anyone knows of any other actions/buttons that could be added?

I would be particularly interested in having a Network or bookmarks icon, btw ;)

And now that we're at it, ayone knows how to:
[LIST]
[*]get rid of the history buttons next to back and forward (little down annoying arrows)
[*]change the hideous icon in the location bar, or get rid of it completely?
[/LIST]
Tx a lot

---

### Post by castawaybcn on 2008-11-14
no one?

---

### Post by Psyphre on 2009-10-21
old thread, but thanks for sharing this info, very handy.
Will share if i find any other things I can add.

---

### Post by chitresh4u on 2010-01-21
Check [this]("http://ubuntuforums.org/showthread.php?t=1158904") thread.

---

