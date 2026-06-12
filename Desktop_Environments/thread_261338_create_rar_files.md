---
title: "create rar files"
date: 2006-09-20
forum: Desktop Environments
---

### Post by z3r0x on 2006-09-20
Hi,

I'm trying to create a multi-volume rar file with the command rar. But I'm not able to, it's always something wrong. I also want to set a password.

Can someone help me?

```

rar -v 286720k -p -u archive.rar folder/

```

---

### Post by Jussi Kukkonen on 2006-09-20
rar wants a command too (a letter without the option switch "-"). This should work for creating/updating 1MB archives:
```
rar u -v1M archive.rar dir/
```

---

### Post by z3r0x on 2006-09-20
ah great :)

One more question. The folder folder/ has some subfolders. How can I add everything (recursive)

EDIT:
I found it sorry (RTFM) :) it is -r

---

### Post by eltech on 2006-10-22
z3r0x, what package did you install to get the ability to create rar files?

---

### Post by hyperair on 2007-11-28
The program used would probably be "rar", found in the multiverse repository.

---

### Post by mm2004 on 2008-03-01
Hi just an update to your question i have created this gui dialog to do exactly what you are trying to do as i have seen no end ov questions like yours about it. all that is needed for this program to work is rar, zenity (installed default in ubuntu), and cksfv this is required to make the .sfv file for checking the clarity of the rars if they are downloaded to say as example. Here take a look

[http://ubuntuforums.org/showthread.php?t=708398&highlight=rar]("http://ubuntuforums.org/showthread.php?t=708398&highlight=rar")

Also if you require to instal these programs just open a terminal and type sudo apt-get install rar unrar cksfv 

ENJOY :)

---

