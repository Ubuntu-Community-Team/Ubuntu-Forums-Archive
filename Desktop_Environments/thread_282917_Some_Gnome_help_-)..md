---
title: "Some Gnome help :-)."
date: 2006-10-23
forum: Desktop Environments
---

### Post by Freddy on 2006-10-23
Hi all. I just recently installed Gnome instead of my usual KDE setup, wanted to try something new while waiting for Kde 4.0. 

I'm having some problems though and some of you might be able to help me (atleast I hope so), okey enough of the chit chat and here we go :-).

After installing a fresh Ubuntu, a couple of drives had changed their name :-). I mounted a fat32 drive in /media/arkiv1 and a ext3 formated drive in /media/arkiv2, but Gnome decided all by itself to put a couple of symlinks to those on the desktop and in that process rename "arkiv1" to "ARKIV2" I guess that is because it's called "arkiv2" in my XP install (and we can't have 2 partitions with the same name now, can we?), but I don't want that here.

Can amyone pls tell me how to rename these links or atleast remove em so I can make my own :-).

Thanks for any help I can get and I think I'm gonna post many questions in the future cause Kde and Gnome isn't even playing in the same ballpark when it comes to how to do things :-).   /// Freddan

---

### Post by ice60 on 2006-10-23
maybe it's this - open -
```
gconf-editor
```

then go to **apps>nautilus>desktop**

and uncheck **volumes-visible**

---

### Post by Freddy on 2006-10-24
Well yeah that sort of helped :-). I have noticed that these drives also shows up in my sidebar to Nautilus. Those links must be taken from my "computer" folder but I don't want that, I want my self mounted and named drives there, not these drives Ubuntu/Gnome have decided the name for.

Thanks for any help I can get.   /// Freddan

---

### Post by canadianwriterman on 2006-10-24
I might be wrong, but I do not believe you can change the name of mounted drives. I have an NTFS partition that Ubuntu picks up and names and I have found no way to change that name.

---

### Post by Freddy on 2006-10-24
> **canadianwriterman said:**
> I might be wrong, but I do not believe you can change the name of mounted drives. I have an NTFS partition that Ubuntu picks up and names and I have found no way to change that name.
If that's the case...it's just dumb. If I want to mount a partition it should be me doing that, Gnome should atleast not name my drives. The way it's setup now is just retared. 

I have mounted my fat32 as arkiv1 in /media but the one picked up in computer Gnome decided to call ARKIV2 and my ext3 drive mounted by me as arkiv2 in /media is named arkiv2. So now I have two arkiv2 drives in my nautilus sidebar and that just feels unprofessional and strange. I would really like to try out and learn my way around with Gnome before going back to kde and flux when 4.0 goes gold, but this really puts me off :-(.   /// Freddan

---

