---
title: "Windows data partitions"
date: 2007-03-26
forum: Desktop Environments
---

### Post by icaruss on 2007-03-26
I'm really thinking about switching to linux but I am worried about my data partitions.  I have about 100gigs of music/movies that I really dont want to have to back up to switch to a linux partition.

If I install ubuntu, will I be able to access my music/movies that are on a windows ntfs partition?

---

### Post by dannyboy79 on 2007-03-26
the short answer is yes. Ubuntu Dapper and Edgy and most all Linux distros can "access" NTFS partitions. They can't "write" to an NTFS partition without the addition of a 3rd party driver called NTFS-3g, there may even be another driver but I am not sure. So no matter what you'll be able to access your music/movies by reading them. if you want to be able to write to that partition you'll have to follow this: [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

Welcome to linux then!!!

---

### Post by icaruss on 2007-03-27
Thanks for your help!

---

### Post by isaacjoe on 2007-03-27
I would really reccomend trying Linux out. There are some bumps and some hiccups that don't exist on windows, my laptop's hardware isn't supported beautifully, you might install it, hate it and gradually drift over in the next few years. Who know! Just install it up, you'll feel lost and powerless at first but as you grow in your knowledge you will get more comfortable and happy with it. But everyone knows that, since I'm talking about the principle of learning something new. Just do it

---

### Post by kanha on 2007-03-28
also,i think that you should try to convert your ntfs drives in fat32 first (while in windows)
then install linux

---

### Post by dannyboy79 on 2007-03-28
I would NOT recommend this of course you are absolutely sure you are never going to want to save a file over 4gb on this partition because this is a limitation of fat32. You can use ntfs-3g as I already suggested or create a ext3 partition and use the fs driver within windows to have access to the files. Of course don't ever save anything on this from windows that requires file permissions and ownership because I believe this is a restriction of the fs driver but I could be wrong. if it's just for movies, documents that you don't care who reads them, music and such than this would be ok. I myeslf have all 3 partitions, fat32, ntfs, and ext3. I haven't written to the ntfs yet but I have used the fs driver and I was able to trnasfer 7 gb of music to it and as long as you "unmount" it correctly within windows than everything is fine when you open it up within linux. BUt if you don't unmount it properly in windows, you may have to run a fsck on it to be able to use it again in linux. also, if you crash in linux, then try to to access in windows, it won't work either. you always have to unmount it properly to be able to use it. good luck.

---

