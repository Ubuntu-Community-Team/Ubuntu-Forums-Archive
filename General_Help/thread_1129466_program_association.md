---
title: "program association"
date: 2009-04-18
forum: General Help
---

### Post by jzacsh on 2009-04-18
Hello, I'm getting some quirky behaviour: when I click Places > **folder** in the top panel of my desktop GIMP tries to launch them. obviously GIMP can't open a folder so I get this error:
Opening '/home/jzacsh' failed: Is a directory

I don't know what I did to make the default application for these folders GIMP instead of Nautilus (*I'm guessin is what happened*), but I know for sure that it only does it with folders (including those mounted from the network such as a WindowsXP folder). On the other hand, if I click "My Computer" or "Network" then Nautilus **will** launch.

*FYI: I'm pretty new to Linux but I'd prefer trying fixes via the terminal (if its not too unrealistic) as I'm studying computer science. I'm using Ubuntu 8.10.? (not sure how to check which version more specifically) and I'm up to date according to Update Manager*

---

### Post by Brucevdk on 2009-04-19
> **jzacsh said:**
> I don't know what I did to make the default application for these folders GIMP instead of Nautilus (*I'm guessin is what happened*)

Most likely this is indeed what happened, i.e. you changed the default association for the mimetype directory. This happens in the GUI when you go to the properties of a folder/file, the Open With tab and select a different application. You can also correct it here.

If you're interested, take a look at the file ~/.local/share/applications/mimeapps.list which stores these associations, it should contain a line which looks something like:

```

inode/directory=gimp.desktop;nautilus-folder-handler.desktop;

```

As gimp comes first it is the default association, you can either remove the line entirely or edit it accordingly.

> **jzacsh said:**
> On the other hand, if I click "My Computer" or "Network" then Nautilus **will** launch.

That's because the Computer and Network locations are not folders but virtual views.

---

### Post by jzacsh on 2009-04-19
Awesome, this solved it both for GUI and Command line. Thanks!

---

