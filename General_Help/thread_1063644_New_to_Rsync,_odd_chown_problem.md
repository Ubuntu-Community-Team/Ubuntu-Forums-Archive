---
title: "New to Rsync, odd chown problem"
date: 2009-02-08
forum: General Help
---

### Post by supergrover1981 on 2009-02-08
Hi gang,

I've just started using rSync & for the most part, it's a life-saver. There's just one little problem that I can't seem to figure out.

On my local machine, rsync'ed files have chown/chgrp root:root. On the remote server, they're (supposed to be) myusername:myusername.

Even if I manually chmod a file to myusername:myusername on the remote server, then rsync down (-rvz), then rsync back up (-rvz), it goes back to root:root on the remote.

I'm guessing there's an easy solution to all this, but I can't quite figure out what it is. Any suggestions most appreciated. :-)

Cheers,
      - SuperGrover

---

