---
title: "Installed LXDE. Now the file manager doesn't recognize any file types."
date: 2009-12-22
forum: Desktop Environments
---

### Post by GoonerLander on 2009-12-22
I was using Gnome, but I installed LXDE to see how the performance would change. It's great, but unfortunately now the file manager doesn't know what file types to assign anything. .jpgs, .avis, .zips -- they're all "unknown". And for some reason under LXDE I can't assign a choice permanently; the usual check-box is absent.

That's pretty much it. I'm guessing this is going to be really easy to fix, but I can't figure out how to do it.

A minor issue, but there it is.

---

### Post by MooPi on 2009-12-22
I use the same file manager and have the same issue but, I'm not concerned. But for the sake of helping I'm investigating a solution. It seems that if the file is marked as executable, a permanent file association can be fixed. Without that you have to pick each time you want to open a file. Don't recommend making all your files exec. Still looking.

---

### Post by MooPi on 2009-12-22
I believe this is a bug, but will probably go without a bug fix until next version is complete. Developer has issued this statement:
> Due to some limitations and unresolved bugs of the original PCManFM included in LXDE, its author, &#27946;&#20219;&#35565; (Hong Jen Yee), decided to totally redesign and rewrite the whole program. Currently there is already some [visible progress]("http://pcmanfm.sourceforge.net/sf.net/projects/libfm"). So unless there are critical bugs or security problems, the original PCManFM 0.5.1 won't be updated recently. Nor will bug reports or feature requests be handled now. So hold your breath, stay tunned, and give us some time.
Help is around the corner:
> If everything goes smoothly, the next generation PCManFM should be ready for release at the end of 2009 or Q1 of 2010.

---

### Post by shae on 2009-12-23
I believe they released a bugfixed version not in the repos (0.5.3?)

---

### Post by SushiR on 2009-12-23
There's a ppa somewhere that has a bugfixed build. Try googling...

---

### Post by MooPi on 2009-12-23
Some Arch users rolled back to a previous version for the fix. I'll stick as it's not that large of an inconvenience.
Another thread a solution for 64bit users [http://ubuntuforums.org/showthread.php?t=1288265](http://ubuntuforums.org/showthread.php?t=1288265)

---

