---
title: "rtorrent - hash check and bad chunks"
date: 2009-06-13
forum: General Help
---

### Post by stando007 on 2009-06-13
Hi,

I have ubuntu 9.04 and i am using rtorrent because it has command line interface and watch directory for download feature. But I have found sometimes (maainly when I am downloading big amount of data in one torrent) it is throwing this error:

```
   Riddick.Trilogy[2006][Director's.Cut]DvDrip-aXXo
  [OPEN]    1850.8 / 1852.3 MB Rate:   0.0 /   0.0 KB Uploaded:    75.2 MB                 [T  R: 0.04]
  Inactive: Hash check on download completion found bad chunks, consider using "safe_sync".

```

I have enabled safe sync in configuration:

safe_sync = yes

But it did not help.

Can somebody help me with this? I am using rtorrent from ubuntu repositories.

---

### Post by kakka256 on 2009-06-26
I'm having the same issue on my 8.10 server version. 
I too have set safe_sync =  yes in config file without any difference.

Forcing recheck of hash (ctrl+r) usually makes the file download completely, but i dont feel that to be a solution to the problem. I would like the file to be completely downloaded without my interaction :)

I don't think my RAM is bad, big downloads has worked before  (e.g. ktorrent downloads files fine), only rtorrent reports bad chunks.

---

### Post by hibliss on 2009-06-26
I have never had this issue before, but have seen it. 

Stop and restart the torrent, or force recheck and it should complete.

How are your partitions formatted (ext3 or ext4?).

---

### Post by kakka256 on 2009-06-26
I am using xfs actually.

And yes, that is what I said, forcing recheck usually "fixes" the problem.  The thing is, I don't want to have to check the status of ongoing downloads every now and then just to make sure they're still running.

Something must be causing the bad chunks...

---

### Post by hibliss on 2009-06-27
According to the author of the software it has to do with the filesystem.

It is a 3 year old issue with no solution.

[http://libtorrent.rakshasa.no/ticket/483]("http://libtorrent.rakshasa.no/ticket/483")

---

### Post by doviende on 2011-10-10
I just ran into this bug myself, on a fresh install of Ubuntu 11.04. According to that bug link listed, there's a possible workaround. You add this to your ~/.rtorrent.rc file:

```
max_open_files = 64
```

Sometimes it seems to also work if I press ctrl+r on a torrent to recheck it.

---

