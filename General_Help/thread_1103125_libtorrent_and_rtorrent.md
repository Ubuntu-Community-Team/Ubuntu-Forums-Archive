---
title: "libtorrent and rtorrent"
date: 2009-03-22
forum: General Help
---

### Post by alexlaban on 2009-03-22
Well I decided to install libtorrent and rtorrent on my server but I can't get it to work. I started following this guide: [http://www.ubuntugeek.com/how-to-install-the-latest-rtorrent-and-libtorrent.html](http://www.ubuntugeek.com/how-to-install-the-latest-rtorrent-and-libtorrent.html) 
Now I'm at the point where I write sudo make for libtorrent but I get these errors. 
```
file_list_iterator.h:64: error: 'abs' is not a member of 'std'
make[4]: *** [file_list_iterator.lo] Error 1
make[4]: Leaving directory `/home/nifelheim/libtorrent-0.12.2/src/torrent/data'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/nifelheim/libtorrent-0.12.2/src/torrent'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nifelheim/libtorrent-0.12.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nifelheim/libtorrent-0.12.2'
make: *** [all] Error 2

```
I've gotten some other errors on the way which I managed to solve with googling but now I'm stuck and I don't find anything on google.

---

### Post by dgrebb on 2009-05-29
Howdy,

These patches solved the problems above; glhf :)

[http://libtorrent.rakshasa.no/attachment/ticket/1266/libtorrent-gcc43-v2.patch]("http://libtorrent.rakshasa.no/attachment/ticket/1554/rtorrent-0.8.2-g%2B%2B4.3.patch")
[http://libtorrent.rakshasa.no/attachment/ticket/1554/rtorrent-0.8.2-g%2B%2B4.3.patch](http://libtorrent.rakshasa.no/attachment/ticket/1554/rtorrent-0.8.2-g%2B%2B4.3.patch)

---

### Post by panGa on 2009-06-05
> **dgrebb said:**
> Howdy,

These patches solved the problems above; glhf :)

[http://libtorrent.rakshasa.no/attachment/ticket/1266/libtorrent-gcc43-v2.patch]("http://libtorrent.rakshasa.no/attachment/ticket/1554/rtorrent-0.8.2-g%2B%2B4.3.patch")
[http://libtorrent.rakshasa.no/attachment/ticket/1554/rtorrent-0.8.2-g%2B%2B4.3.patch](http://libtorrent.rakshasa.no/attachment/ticket/1554/rtorrent-0.8.2-g%2B%2B4.3.patch)How do I use the patch?

---

### Post by Chronon on 2009-06-06
Use the [patch]("http://linux.die.net/man/1/patch") program to apply it to the source tree.  Then build the source.

---

