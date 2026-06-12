---
title: "Moving house"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-22
:smile:  I like making up thread titles 

If I wanted to move /home onto it's own seperate partition so that the actual drive was /home not /home was a folder on the drive (unless that's how it would've been by doing this at install stage).

I saw you can move /home from control panel, but i didn't know if that was enough

The reason is to share all program config files with win2k (so we need fat32-ness)

Also, while i'm chopping my disk up, I may as well make a swap partition and turn it on. /swap doesn't seem to be a mount point, so I@m thinkin this will be a different procedure.

Not to brag, but i think i'm gettin this quite quick  :smile:

---

### Post by uidzer0org on 2005-06-22
check out /etc/fstab and create an entry for the hdd pointing to /home after you have copied the files over

---

### Post by davahmet on 2005-06-22
I don't think there is anything that prevents you from putting /home on a FAT32 partition, it's just an extremely bad idea.  I believe you may not like the results that come from doing this.

The problem is with ownerships and permissions.  Linux uses filesystem ACLs to assign ownership and permissions to files, directories and symlinks.  Unfortunate, this concept isn't really applicable in the Windows world, so putting files on a FAT32 partition should give it root ownership with wide-open permissions.  You might say, "so what.  I like having a Windows security model" but the problem then becomes that your .profile, .bash_profile and or .bashrc is no longer owned by you.  Without these important files, you may face instability or complete failure to log on.  I've never tried it so I'm not sure how bad the results would be.

Putting /home on FAT32 may seem like a convenient idea, but certainly it is an experiment only for the adventurous.

---

### Post by desdinova on 2005-06-22
[QUOTE=davahmet]I don't think there is anything that prevents you from putting /home on a FAT32 partition, it's just an extremely bad idea. I believe you may not like the results that come from doing this.

The problem is with ownerships and permissions. Linux uses filesystem ACLs to assign ownership and permissions to files, directories and symlinks. Unfortunate, this concept isn't really applicable in the Windows world, so putting files on a FAT32 partition should give it root ownership with wide-open permissions. You might say, "so what. I like having a Windows security model" but the problem then becomes that your .profile, .bash_profile and or .bashrc is no longer owned by you. Without these important files, you may face instability or complete failure to log on. I've never tried it so I'm not sure how bad the results would be.

Putting /home on FAT32 may seem like a convenient idea, but certainly it is an experiment only for the adventurous.[/QUOTE]

I'd second the "disaster" .... as FAT32 has no concepts of permissions its very likely things like X and the like are just not going to work.

---

### Post by Dave_is_sexy on 2005-06-22
Oh. Well thanks I wont do that then. I'll erm... (thinks)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Would this be a better idea? It doesn't support security either tho. Am i to understand there is no way of having a common dynamic local ical file? for example.

I am completely willing to learn  :smile:

---

### Post by desdinova on 2005-06-22
Its incredibly unlikely any method will completely integrate the permissions, if you think about it - They can map Linux "root" to Windows "administrator" - but what about the rest of the users? Groups?

It'll probably work fone for thinks like a shared ical file, (for example) but I wouldn't use it for a lot of things. Moz can share profiles, but be cautious when one writes to the other filesystem without knowing what user to write as

---

### Post by Dave_is_sexy on 2005-06-22
I see. I'm really hoping to share all application profiles and emails and things - and a common download area for Azureus so that linux and windows can pick up each others downloads. Downloding the Debian 3.1 DVDs is a pain when it only works in 1 OS and i'm switching between 2

Of course FAT32 will be fine for that, but I hve a thread around here somewhere abut the Captive wrapper for things that need to be secure  :)

---

