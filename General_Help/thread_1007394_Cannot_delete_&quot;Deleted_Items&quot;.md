---
title: "Cannot delete &quot;Deleted Items&quot;"
date: 2008-12-10
forum: General Help
---

### Post by Graham1 on 2008-12-10
Hi

I'm having problems deleting my "Deleting Items". It reports "Permission denied" when I try to do so. How can I delete these items?

:)

---

### Post by fooman on 2008-12-10
do you mean the items in your trash?

if so,  try this in a terminal:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by Graham1 on 2008-12-10
Yes. I tried the command below but the items are still in the Trash. If this helps, the items deleted were from a mounted drive (i.e /mnt/data).

:)


> **fooman said:**
> do you mean the items in your trash?

if so,  try this in a terminal:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by drs305 on 2008-12-10
Probably the safest way to delete the files is to open nautilus with admin priveleges. Use SHIFT-DELETE to remove the files (same applies if they are in $HOME/.local/share/Trash):
```
gksudo gedit /root/.local/share/Trash
```

If the files are located elsewhere just navigate to the applicable folder. Refer to the Trash link in my signature line to learn how to find and delete root trash.

---

### Post by porchrat on 2008-12-10
> **Graham1 said:**
> Yes. I tried the command below but the items are still in the Trash. If this helps, the items deleted were from a mounted drive (i.e /mnt/data).

:)

well then navigate into the directory:

```
cd ~/.local/share/Trash/files
```

Then change their ownership to your username:

```
sudo chown username:username ~/.local/share/Trash/files
```

Where "username" is the name of the user whose trash directory the files are sitting in.

Then (probably not required but you never know) change the permissions to make sure that you can do whatever you want to the files (please make sure in the future that you know what this command does as it can be quite dangerous):

```
sudo chmod 777 ~/.local/share/Trash/files
```

Then try the remove command mentioned previously:

```
sudo rm ~/.local/share/Trash/files/*
```

Also please in future be careful when using the "-rf" flag unless it is seriously necessarily as if you are in the wrong directory when you run this command you could do some serious damage.  For more information on what those flags do check the "rm" command manual:

```
man rm
```

---

### Post by Graham1 on 2008-12-14
Thanks to everyone who replied. Problem now resolved.

:)

---

