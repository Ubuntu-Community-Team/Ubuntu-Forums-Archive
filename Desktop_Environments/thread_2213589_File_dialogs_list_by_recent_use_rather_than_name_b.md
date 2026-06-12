---
title: "File dialogs list by recent use rather than name by default - how to change?"
date: 2014-03-27
forum: Desktop Environments
---

### Post by EarlsFurniture on 2014-03-27
I've noticed a serious annoyance with 12.04, at least the stock Unity version. (this may also exist in Xubuntu and Lubuntu, but I haven't checked)

When trying to Open or Save any file from any app that uses the DE's file dialogs, the dialog lists files and folders inside the current folder by recent use - instead of alpha by name. This is beyond annoying. 99.99999999% of the time, I can't find what I'm looking for quickly, I have to click the file name header to sort accordingly first, and I have to do this EACH and EVERY folder I navigate down into. That is, If say the first list shows ALL files by recent use, then I have to sort by name, and then select a folder (because the file is nested down) then when that folder opens, it is sorted by last use again, (within that folder) and I have to sort by name AGAIN, drill down another folder, etc. Not only do the file dialogs default to "recent use" listing on first opening, they revert to this mode through each and every drill down into nested folders.

Is there a way to change this default behavior? (note, selecting 'sort by name' and 'show folders before files' in Nautilus preferences, does NOT seem to affect file dialogs.) Something similar to the preferences in Nautilus for file dialogs would be what I'm thinking of here.

---

### Post by bapoumba on 2014-03-27
May be this bug ?
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/982742](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/982742)

---

### Post by EarlsFurniture on 2014-04-03
> **bapoumba said:**
> May be this bug ?
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/982742](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/982742)

Yep. Seem like it anyway. Thanks. It appears that the solution is in [comment #6]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/982742/comments/6") there.

I resolved the issue (so far) by modifying my ~/.config/gtk-2.0/gtkfilechooser.ini file as follows:

```
[Filechooser Settings]
LocationMode=filename-entry
ShowHidden=false
ExpandFolders=true
ShowSizeColumn=true
GeometryX=20
GeometryY=54
GeometryWidth=732
GeometryHeight=571
SortColumn=modified
SortOrder=ascending

```

I changed:
```
SortColumn=modified
```
to read:
```
SortColumn=name
```

---

### Post by bapoumba on 2014-04-04
Glad to see you solved it, and thanks for marking your thread as such :)

---

