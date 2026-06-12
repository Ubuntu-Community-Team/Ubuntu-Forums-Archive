---
title: "Icon customization help, gvfs: error setting attribute"
date: 2010-03-02
forum: Desktop Environments
---

### Post by Da_MerV on 2010-03-02
Hello,

I've been trying to figure out some folder icon customization over the past couple days and I can't seem change precisely what I would like.

I understand there is an easy way to set a folder's custom-icon through the Properties window, however, this does not give the effect I am looking for.

By changing the custom-icon, you are only changing metadata::custom-icon as opposed to standard::icon. The issue with this is that this custom-icon is always used, regardless of icon theme changes or zoom.

Here's an example of the scaling issues that arise from this:
This shows the "Templates" folder with it's default icon, and another folder with a custom icon to match at 100% zoom.
[IMG]http://i45.tinypic.com/3003z8y.png[/IMG]
When you change the zoom level, this same 48x48 icon is simply scaled, whereas the "Templates" folder gets the appropriate icon for this zoom.
Here, at 33% zoom, the custom icon is a blurry mess.
[IMG]http://i49.tinypic.com/152faj7.png[/IMG]
And at 200% zoom, the custom icon is different still.
[IMG]http://i45.tinypic.com/rsaj3s.png[/IMG]

Being as much of a pixel-perfectionist as I am, I would like to know how to create or change a folder so that it's icon is changed properly.

I've looked into gvfs-* commands, and found some seemingly relevant information. With a run of gvfs-info on both example folders, I found:
```
merv@***:~$ gvfs-info School/ | grep "standard::icon"
  standard::icon: inode-directory, gnome-mime-inode-directory, inode-x-generic, folder
merv@***:~$ gvfs-info Templates/ | grep "standard::icon"
  standard::icon: folder-templates, folder

```

I tried modifying the standard::icon with gvfs-set-attribute and I receive the following:
```
merv@***:~$ gvfs-set-attribute School/ stardard::icon "folder-templates, folder"
Error setting attribute: Setting attribute stardard::icon not supported

```

Long story short, how might I create or change the actual icon associated with a folder? The attribute is obviously set on folders when ubuntu is first installed, shouldn't it be possible to create new folders with these custom attributes?

I appreciate any information you can share,
Thanks,
-Merv

---

### Post by Da_MerV on 2010-03-10
Any info anyone?

---

### Post by __init__ on 2010-10-13
Bump. I have exactly the same question.

---

### Post by __init__ on 2010-10-13
Well, found solution. Really simple yet it was pretty tricky to find out.

Just edit ~/.config/user-dirs.dirs

---

