---
title: "Deleting Trash"
date: 2006-12-09
forum: Desktop Environments
---

### Post by dudds on 2006-12-09
Hi,

I'm using Gnome as me desktop environment and have deleted a lot of files recently, mainly mp3 files within Amarok. I have emptied my trash can so thought all files had been deleted from my system.

Then today I was exploring the filesystem and playing around with the DU command and found that the directory ~/.local/share/Trash/files was 3.5GB in size. When I listed the contents of this directory I noticed that they were all mp3 files that I had deleted from my collection.

I have two questions:
1. Can I manually delete these files without causing any harm to my sytem; and
2. Why were these files either not in the trash, or deleted when I emptied the trash.

Does it have anything to do with the fact I was using a KDE app (Amarok) within Gnome??

Thanks in advance.

---

### Post by DWright on 2006-12-09
mmmm? odd!
To answer your first question: Yes you can safely delete the folder and the files. (Either using the graphical interface, or dropping to a shell (terminal) and using rm -rf)

It should not be because you are using a KDE app. in a Gnome environment. It may be an obscure bug in Nautilus. I have noticed that if I use Nautilus to "delete" (read: move to "Trash Can") files from a USB thumb drive, the files are moved to the .trash folder on the USB thumb drive, but they do not appear in the desktop "Trash Can"
see: [http://gnomesupport.org/forums/viewtopic.php?t=12051]("http://gnomesupport.org/forums/viewtopic.php?t=12051")

---

### Post by mannheim on 2006-12-09
The gnome trash directory for a user's files is ~/.Trash but the KDE trash directory is ~/.local/share/Trash. So I think what happens is that Amorak moves the files to ~/.local/share/Trash when you delete items. When you "empty the trash" on the gnome desktop, you empty the directory ~/.Trash (which is not where Amorak put this files).

---

### Post by dudds on 2006-12-10
Thanks Mannheim that makes sense.

---

### Post by MCSE_Crossover on 2007-02-09
> **mannheim said:**
> The gnome trash directory for a user's files is ~/.Trash but the KDE trash directory is ~/.local/share/Trash. So I think what happens is that Amorak moves the files to ~/.local/share/Trash when you delete items. When you "empty the trash" on the gnome desktop, you empty the directory ~/.Trash (which is not where Amorak put this files).

Is there a way to redirect this or fix this issue? I notice the same problem when using Digikam through Gnome...

---

### Post by gradedcheese on 2007-02-09
symlinks...

say you want to only have .Trash as the trash (which is what Gnome uses).  But some application insists on .local/share/Trash for its Trash path.  In a terminal:

1) remove the other Trash:

rm -rf ~/.local/share/Trash

2) replace that with a symlink to the real Trash:

ln -s ~/.Trash ~/.local/share/Trash

---

### Post by MCSE_Crossover on 2007-02-13
Excellent information! Good to know for us "newbies." Symbolic links are definately something that us "Microsoft crossovers" don't deal with too much, but obviously, are very important in the Linux realm.

---

### Post by ubunter1 on 2007-02-13
i have trash in the trash icon but it will not delete after using the empty trash text on the right click menu,it deletes pictures mp3s and the like but i have copys of folders and libmtp leftovers from when i installed gnomad.is it safe to delete these?,and how?.thanks.

---

### Post by Kimos on 2008-03-13
> **gradedcheese said:**
> symlinks...

say you want to only have .Trash as the trash (which is what Gnome uses).  But some application insists on .local/share/Trash for its Trash path.  In a terminal:

1) remove the other Trash:

rm -rf ~/.local/share/Trash

2) replace that with a symlink to the real Trash:

ln -s ~/.Trash ~/.local/share/Trash

I was trying to figure out what was eating up so much space in my home folder. Ended up writing a script that output the size of hidden folders, which eventually led to this.

I use AmaroK, Ktorrent, and K3B under Gnome. All three of them moved large media files to that folder which never get erased.

Just wanted to thank you for the fix. The symlink did the job.

---

