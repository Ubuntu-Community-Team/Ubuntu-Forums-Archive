---
title: "Removing old packages"
date: 2006-01-12
forum: General Help
---

### Post by thebadrash on 2006-01-12
Hi,

I'm fairly new to Linux and after trying out Ubuntu, moved onto Kubuntu which I'm really happy with. I have searched for an answer to this question, but perhaps I don't know the correct terminology, so excuse me if it's the most obvious thing in the world!

What I want to know is: how can I ensure that I only have the packages I'm using saved on my hard disk? Two months ago I installed Ubuntu and then KDE. At that point, I had over 2GB free space on the partition I use for linux, and nothing but the system is saving stuff to that drive. Now I have under 1 GB of space, and I can't believe that this is just down to installing a few extra programs. What I want to do is 'clean up' the disk by removing redundant packages... but I don't know for sure which ones are redundant. Is there a disk cleaning tool or a command line I can use to erase unneeded data?

Thanks for your help!

---

### Post by feathers on 2006-01-12
You have to remove the packages by hand. How should a programme know which packages you still require?. I would use adept, search for gnome, as this is something you won't need now and remove the packages. If you start with packages that contain the syllable "lib", a lot of other packages will be removed automatically. Before committing changes you should look at "Preview changes", so you do not deinstall needed programmes.

---

### Post by thebadrash on 2006-01-12
OK thanks a lot. I'll give that a go. I have already removed gnome.

I suppose I thought that a program or command might be able to look at the packages stored in system folders and then cross check them to see if any of them are 'floating' - not relied on by any other application. Or something :)

---

### Post by feathers on 2006-01-12
Sure you can do that, with the command "deborphan". But you will probably not have very many packages like that. By removing gnome you will not have removed many packages, if any at all. Gnome is a metapackage which means that it depends on a lot of other packages but these packages will not be removed if the metapackage is removed.

---

