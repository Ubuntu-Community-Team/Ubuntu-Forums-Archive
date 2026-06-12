---
title: "XFCE/Thunar Compact List View in Nautilus?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by GenPFault on 2006-06-09
New whole-hog (whole-drake?) Ubuntu convert here.

Is it possible to get a [Thunar]("http://thunar.xfce.org/index.html")-style [Compact List View]("http://thunar.xfce.org/news.html#2006-04-16") in Nautilus?  I've also seen this described as "multi-column list view" and simply "List View" in Windows Explorer.  

I find this particular style of file management extremely efficient for large collections of files/directories, especially coupled with find-as-you-type selection.

---

### Post by Sutekh on 2006-06-09
Why not try out Thunar yourself?
```
sudo apt-get install thunar
```
You may decide its better than Nautilus (which I don't believe does this compact view thing) and keep it.

---

### Post by GenPFault on 2006-06-09
[QUOTE=Sutekh]Why not try out Thunar yourself?
```
sudo apt-get install thunar
```
You may decide its better than Nautilus (which I don't believe does this compact view thing) and keep it.[/QUOTE]
Thanks!  Is there any way to get Thunar to act as a replacement for Nautilus?

---

### Post by Sutekh on 2006-06-09
Sure, just use it instead of Nautilus?  I think it does most things that Nautilus does.  I'm not sure I know what you mean.

---

### Post by GenPFault on 2006-06-09
[QUOTE=Sutekh]Sure, just use it instead of Nautilus?  I think it does most things that Nautilus does.  I'm not sure I know what you mean.[/QUOTE]
Sorry, I wasn't being very clear.  I meant using Thunar wherever Nautilus might be invoked, either for file or desktop management.  However, I just checked and it seems that Thunar doesn't support the pseudo-URIs (fonts://, smb://, ssh://, etc.) that Nautilus does, so that's a non-starter.  It looks like there's a [Gnome-VFS FUSE module]("http://sole.infis.univ.ts.it/~chri/gnome-vfs-fuse-0.1.tar.gz") that might work toward that end, but the semantics aren't quite the same.

Anyway, thanks for the help!

---

### Post by tfm_copycat on 2008-06-23
This is a new feature to be implemented in a future version of nautilus.
If you want to try the development version, [follow this tutorial]("http://www.zdi.it/?p=11")

:popcorn:

---

