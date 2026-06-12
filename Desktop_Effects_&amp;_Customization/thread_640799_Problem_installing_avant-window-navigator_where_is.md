---
title: "Problem installing avant-window-navigator where is public key ??"
date: 2007-12-14
forum: Desktop Effects &amp; Customization
---

### Post by frojnd on 2007-12-14
I'm on gutsy and I  added :
```

deb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

But than when I've tryed to update there was an error: 
```
W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: http://download.tuxfamily.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
If you want to fix this problem try sudo apt-get update.
```

I've tryed to update twice but the same error, also there is no package avant*

Any ideas how to fix this and install avant-window-navigator via deb ?

---

### Post by PinkFloyd102489 on 2007-12-14
```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```

---

