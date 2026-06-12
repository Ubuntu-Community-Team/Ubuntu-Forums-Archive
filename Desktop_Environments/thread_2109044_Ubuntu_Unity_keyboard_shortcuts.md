---
title: "Ubuntu Unity keyboard shortcuts"
date: 2013-01-26
forum: Desktop Environments
---

### Post by codephobic on 2013-01-26
Hi,

I've been customising my shortcuts quite a bit, over the past few months and I often install multiple instances of ubuntu (and other linux oses), so I was wondering whether it is possible to export (and import) keyboard shortcuts?


Thanks

---

### Post by grahammechanical on 2013-01-26
Stop and think for a moment. These changes that you make, they have to be stored somewhere. True? In a script in some folder? Find the folder. find the script and copy it into the other versions.

It will be somewhere in the home folder. Most likely in a folder that is hidden. Set the File Manager View option to Show Hidden Files. And start looking.

Regards.

---

### Post by codephobic on 2013-01-26
> **grahammechanical said:**
> Stop and think for a moment. These changes that you make, they have to be stored somewhere. True? In a script in some folder? Find the folder. find the script and copy it into the other versions.

It will be somewhere in the home folder. Most likely in a folder that is hidden. Set the File Manager View option to Show Hidden Files. And start looking.

Regards.
Well yes, it had occurred to me that the shortcuts might be stored somewhere in a flat file, "behind the scenes". I just wanted to know whether there was an export/import mechanism much like that for favourites/bookmarks in browsers and if not whether there was a usable hack substitute.

For all I know (and, if you hadn't guessed by now, that is pretty little when it comes to linux desktops) it could be stored in some obscure folder buried deep within some part of /lib /etc /usr/... etc etc etc.

---

### Post by gifford on 2013-01-26
Try looking here: ~/.gnome2/accels/

---

### Post by codephobic on 2013-01-27
> **gifford said:**
> Try looking here: ~/.gnome2/accels/

Thanks, I'll have a look there today.

There are tonnes of folders and the linux file system doesn't seem to have much of a consensus on where exactly config files should reside, so it just struck me as exactly the sort of question to ask people at ubuntu forums, rather than spend hours trying to find something that may or may not be stored in the way I assumed.

---

### Post by codephobic on 2013-01-27
> **gifford said:**
> Try looking here: ~/.gnome2/accels/

I had a look in the directory, there was only one xml file which had only a selection of the keyboard shortcuts that are configured for my system. None of my own custom shortcuts are there.

I'm very surprised at the lack of google hits for this query, can't find anything at all.

---

