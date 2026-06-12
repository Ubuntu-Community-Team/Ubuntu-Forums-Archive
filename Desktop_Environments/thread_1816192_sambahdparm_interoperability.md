---
title: "samba/hdparm interoperability"
date: 2011-08-01
forum: Desktop Environments
---

### Post by MG2R on 2011-08-01
Don't know if this is the right place for my question...

I have a self-built NAS running ubuntu 10.04LTS desktop. I have samba on it to be able to connect to my drives from windows. I als have hdparm installed to spin down my drives when I'm not using them (I know it's healthier to let them spin, but since this thing is in my bedroom it needs to be absolutely silent when I'm sleeping, it's completely passively cooled).

Now the problem is that when I watch a movie, it happens that a big part of the movie gets buffered while I'm watching and my drives aren't used for such a long time that they spin down. Of course a few minutes later my drives have spin up again to stream the rest of the film. This way my drives spin up and down a lot and this isn't ideal.

So I was hoping it is possible to let samba tell me (and by me I mean a script) that there are clients connected (even though they are not using the drives). That way the script can tell hdparm to spin up the drives when clients are connected and spin down when no client is connected.

I hope this is possible in any way.

Thanks!

---

