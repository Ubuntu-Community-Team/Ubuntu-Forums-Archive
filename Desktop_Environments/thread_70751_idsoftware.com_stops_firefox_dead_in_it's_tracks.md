---
title: "idsoftware.com stops firefox dead in it's tracks"
date: 2005-10-01
forum: Desktop Environments
---

### Post by websavages on 2005-10-01
I'm running hoary with the latest and greatest version of firefox. everytime i surf to [www.idsoftware.com](www.idsoftware.com) firefox freezes.

can anyone replicate this, just to confirm it's not my setup?

Cheers ws

---

### Post by Memphis on 2005-10-01
Try going into Synaptic Package Manager and doing a search for 'flash'.

I had a similar issue which turned out to be multiple installations of different flash programs such that when I visited a site with any flash content, it would crash firefox.

Try removing all versions of flash and then installing just the one.

---

### Post by websavages on 2005-10-01
Apparently it's a bug in the flash plugin provided by the universe repo. see [here](https://launchpad.net/distros/ubuntu/+sources/libflash/+bug/302).
Solved it by downloading the tarball from macromedia and installed that. 
Cheers ws

---

