---
title: "Extract here"
date: 2007-04-03
forum: Desktop Environments
---

### Post by MrZehl on 2007-04-03
I'm using Ubuntu Feisty beta.
When I right click in the file browser on an archive and choose the option 'extract here', I expect that the file is extracted in the current directory. This isn't what happens. When I extract archive.rar, a directory is created with the name archive.rar_FILES and the files will be extracted in this direcory.
That is not what I want. I want the files extracted the current directory. 

How can I make this menu item making work the way I expect and the way I want?

---

### Post by ComplexNumber on 2007-04-03
> **MrZehl said:**
> I'm using Ubuntu Feisty beta.
When I right click in the file browser on an archive and choose the option 'extract here', I expect that the file is extracted in the current directory. This isn't what happens. When I extract archive.rar, a directory is created with the name archive.rar_FILES and the files will be extracted in this direcory.
That is not what I want. I want the files extracted the current directory. 

How can I make this menu item making work the way I expect and the way I want?
 right click on the tarball, select Open with Archive Manager(if archive manager isn't an option, select Open With Other Application), then tick OFF 'Recreate Folders'

---

### Post by taurus on 2007-04-03
Do you get the same thing if you extract it from a terminal?

```
unrar x archive.rar
```

---

### Post by MrZehl on 2007-04-03
No... 'Extract here' creates default  a directory of  the filename with _FILES extended. 
This directory isn't in the archive. Most of the times ther is already a directory in the archive and that is exactly why I don't want this command to make another one. Then the directory in the archive is placed in the directory archive.rar_FILES. 
It doesn't happen when I open the archive and extract from there. But this menuitem should make it easy.

The directory in the archive should be created in the current directory as 'Extract here' implicates. 
The way it currently works the menu item should be called 'Extract in archive.rar_FILES' This should be a file dependant named menuitem. But I don't want to rename the menu item, I want the current working as expected.

---

### Post by MrZehl on 2007-04-03
> **taurus said:**
> Do you get the same thing if you extract it from a terminal?

```
unrar x archive.rar
```

This works as I expect 'Extract here' should work. No extra directory is created.
Where can I find the command that is executed by the menuitem 'Extract here'? That is what should be changed. 
I'm rather new to Linux and have no clue where to look. Which configuration file I've to adjust?

---

### Post by MrZehl on 2007-04-03
> **ComplexNumber said:**
> right click on the tarball, select Open with Archive Manager(if archive manager isn't an option, select Open With Other Application), then tick OFF 'Recreate Folders'

I want to recreate the folders in the archive. I just don't want to create an extra one.

---

### Post by ComplexNumber on 2007-04-03
> **MrZehl said:**
> I want to recreate the folders in the archive. I just don't want to create an extra one.
 it was unclear what you were wanting because extract here works perfectly for me. the problem is probably more to do with the way it was archived.
note that, if there is a file as well as a directory in the archive, the 'extract here' option will place them in a directory by default.

---

### Post by MrZehl on 2007-04-03
> **ComplexNumber said:**
> it was unclear what you were wanting because extract here works perfectly for me. the problem is probably more to do with the way it was archived.

That's not the case. It happens with all archives since I use Ubuntu. Could be a fenomenal coincidence, but I don't belive that. And like I said earlier 'unrar x archive.rar' doesn't create that directory. It isn't included in the archive. The directory doesn't show in archive manager either.

I admit that it's strange that I've the problem and others not, but it's there.

Where are the configuration files stored for the right click menu for file maneger? Or is it a Gnome config file? If so, where?

---

### Post by MrZehl on 2007-04-07
I've found a workaround by using a custom script here. 
[http://ubuntuforums.org/showthread.php?t=28642](http://ubuntuforums.org/showthread.php?t=28642)

But it is still a working around. Is there any way to edit the default menu item 'Extract here' ? There must be since previous posts in this thread make clear that some people don't have the problem I encounter. 
So their installation of nautilus seems to be different from mine. What is the difference?

---

### Post by fordfan753 on 2007-04-07
You'll be happy to know that Edgy has the functionality you're asking for.

---

### Post by MrZehl on 2007-04-07
> **fordfan753 said:**
> You'll be happy to know that Edgy has the functionality you're asking for.

Edgy? I'm using Feisty and it should work in Feisty. I'm not going to switch to Edgy to make a menuitem work the way I want. The way it should actually.

---

### Post by fordfan753 on 2007-04-08
Oops, I'm wrong. I just got my edgys confused with my feistys. It works for me that way on feisty last time I checked.

---

### Post by MrZehl on 2007-04-11
Todays update fixed it. :)

---

### Post by AstralEagle on 2008-01-10
As one of the previous posters requested, I would also like to know how to edit the "Extract Here" menu item, or, preferably, create a new one.
Since I'm assuming this menu item is just a shortcut to a command, I should be able to edit it or add another one.
I'm thinking an "Extract to Desktop" command would be useful.

:)

---

