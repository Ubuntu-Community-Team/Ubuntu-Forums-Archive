---
title: "How to search through sub directores?"
date: 2007-05-12
forum: Desktop Environments
---

### Post by timzak on 2007-05-12
I'm trying to search for all PNG files on my Filesystem, including all subdirectories.  Can't figure out how to do that in Nautilus.  Help?  When I type .png in the search bar, it only searches the root directory.

Thanks.

---

### Post by mexlinux on 2007-05-12
You can try konqueror
If you type png in the address bar, it will search for all the png files in your filesystem.
If you are in browser mode, syply type: locate:png
ready

---

### Post by taurus on 2007-05-12
Applications -> Accessories -> Terminal
```
sudo find / -name *.png -print
```

---

### Post by hartz on 2007-05-12
If you want to search for files "*.png", "*.PNG" and variations like "*.Png", use this command in a terminal.

```
find / -print | grep -i "png"
```

However if you have a lot of files they may rush by, possibly in great splurts.

This will allow you to take control of the text scrolling past:

```
find / -print | grep -i "png" | less
```

If you want to search starting with a directory other than the root, you can specify it as the first argument after the "find" command, like this:

```
find /dirname -print | grep -i "png"
```

You can even specify multiple directories

```
find /path1 /path2 /path3 -print | grep -i "png"
```

Or to simply start search from the directory where you are at that moment.
```

find . -print | grep -i "png" | less
```

These commands will also list all the files in directories where there is "png" anywhere in the path.  To limit to **only finding files that ends in a png extention**, use a "$" in the grep search string like this

```
find . -print | grep -i "png$" | less
```

the find command ... finds files.

the "grep" command filters out things you don't want.

the "less" command (as in less is more) controls text which is "more" than what will fit on the "terminal winndow".

And finally, the | (pipe) symbol links the output from one command into the next command on the line.

---

### Post by timzak on 2007-05-12
Thanks for all the tips.  So Nautilus can't do this on its own?  I would think all it would need is an option to "search all sub directories" and you'd just start your search at root.

---

### Post by taurus on 2007-05-12
The only problem is that you didn't start nautilus as root.  You started it with your login account.

```
gksudo nautilus
```

---

### Post by hartz on 2007-05-14
> **taurus said:**
> The only problem is that you didn't start nautilus as root.  You started it with your login account.

```
gksudo nautilus
```

I think running nautilus as root is a really really bad thing.

You can do it occasionally when you have no other way to accomplish a task (????), but don't get into the habit - you could break your installed linux, circumvent all the security measures, and make fatal mistakes much too easily with this little "trick".

---

