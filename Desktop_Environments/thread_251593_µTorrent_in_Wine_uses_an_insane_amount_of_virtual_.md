---
title: "µTorrent in Wine uses an insane amount of virtual memory!!!"
date: 2006-09-05
forum: Desktop Environments
---

### Post by srunni on 2006-09-05
Hi,

I'm running µTorrent in Wine, and while the total RAM consumption for utorrent.exe and explorer.exe is only about 9 MB, the virtual memory consumption is insane! utorrent.exe and explorer.exe each use more than 2,600 MB of virtual memory, which adds up to 5 GB of virtual memory used just by them!! Is this really necessary, or is it a bug? By comparison, the 3rd highest consumer of virtual memory, xorg, only uses 192 MB of it.

Thanks for the help!

---

### Post by croak77 on 2006-09-05
You are running a windows program in linux. There might be some problems. Try using a native torrent client like rtorrent instead.

---

### Post by Rhapsody on 2006-09-05
It certainly does sound rather strange to that µTorrent would eat up so much swap space and so little memory, even when run under Wine. But why not just use KTorrent? It's got most of the features in µTorrent, and is included with Kubuntu.

---

### Post by srunni on 2006-09-06
Well, I'm just used to µTorrent. And as for KTorret, I haven't tried it, but I might. However, according to an article I read (I think on torrent-freak) only µTorrent and Azureus have a certain 9 features, many of which I use. But maybe KTorrent will have the particular features I use, so I'll have to look into that.

---

