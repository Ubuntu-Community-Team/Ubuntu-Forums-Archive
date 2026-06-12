---
title: "Wine - Moving drive_c without screwing things up?"
date: 2007-07-22
forum: Gaming &amp; Leisure
---

### Post by ironfistchamp on 2007-07-22
Hey people,

I am installing games with Wine (so far so good) but one of then, Guild Wars, is gonna take a lot of space, which I don't have on my home drive. Is there so way I can move the drive_c easily without messing it all up. I don't want to have to reinstall everything in wine just because I am going to run out of space.

Any ideas people? I am not very knowledgeable when it comes to this.

Thanks

Ironfistchamp

---

### Post by hikaricore on 2007-07-22
Instead of moving the whole thing why don't you just make a symlink for the GuildWars directory?

> 
cd ~/.wine/drive_c/Program\ Files
ln -s /media/drivelocation/GuildWars


Where /media/drivelocation/GuildWars is the existing location you will be installing.
This has to be an actual location, you can't just type this exactly, I just needed something to use as a placeholder.

---

Aside from that errmm... you **CAN** just install the game on a different drive from the installer itself.
Not everything has to be in your WINE directory, this just keeps things organized, but if space is limited put it elsewhere and leave your drive_c alone.

---

### Post by ironfistchamp on 2007-07-22
Thanks thats good. What it is is that Guild Wars is already installed but I want to run it with the -image switch to download all the files. That would fill up the hard drive it is currently on but not another I just wondered if I could move it and get it to download the lot onto the new hdd. I assumed moving drive_c would do that.

---

### Post by cogadh on 2007-07-22
hikaricore's suggestion should work fine, but, for future reference, you can move your .wine directory wherever you want, just make sure you run "wineprefixcreate" after you do it to tell Wine where the directory is now.

---

