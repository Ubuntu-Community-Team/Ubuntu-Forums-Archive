---
title: "Mounting a folder on an ntfs partition"
date: 2006-06-21
forum: Desktop Environments
---

### Post by kingmob on 2006-06-21
I realise this is not really an ubuntu question, but i suspect i might be able to get the answer here ;)

I have mounted all my windows partitions in fstab no problem, but i don't use all those folders. So, for the coolness factor and because it'll be clearer, i want to only mount specific folders. So i want a /media/mp3 folder, where /media/D/mp3/ is mounted. So D is one of my drives, but the only folder i would want to automount at the start is mp3. How do i do this in fstab?
If it's only possible by first mounting D that would also be ok.

Thanks in advance

---

### Post by RRS on 2006-06-21
You could probably create a link to the folder on your desktop or panel just as if it were in your Ubuntu partition.

I think I've also seen directions somewhere to remove the patition icon from the desktop. 

This should give the desired results, but someone else may have a more efficient method.

---

### Post by Loffe_ on 2006-06-21
You only need to mount /media/D once.

Try making a link to to /media/D/mp3 if you want to show up in /media

When /media/D already is mounted
```

cd /media
sudo ln -s /media/D/mp3

```

---

### Post by kingmob on 2006-06-21
I was thinking along those lines as well. But then there is no way to mount it without mounting the whole D partition?

---

### Post by Loffe_ on 2006-06-22
[QUOTE=kingmob]I was thinking along those lines as well. But then there is no way to mount it without mounting the whole D partition?[/QUOTE]

You have to mount the filesystem to get access to the files! (If you aren't using special repair utilities or something like that I think)

---

