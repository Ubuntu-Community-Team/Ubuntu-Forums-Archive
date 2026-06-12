---
title: "bittorrent too slow"
date: 2005-11-23
forum: Desktop Environments
---

### Post by pirozzi on 2005-11-23
i've just installed bittorrent / bittornado but i can't use it because it is too slow. i've read that could be due to firewall setting but i don't know how to set it in a more proper way.

---

### Post by narcolept on 2005-11-23
The transfer speeds are slow?  The premise of bittorrent is that you start slow, and ass you grab parts of the file to transfer to others, your speeds increase. download speeds are tied to upload speeds exponentially with bittorrent.  Try letting it sit till you get some of the file to transfer to others, and your speeds should increase.  It's not uncommon to see speeds between 1-5KB/s for a while until you ramp up on a torrent.

---

### Post by pirozzi on 2005-11-23
sure i have some stuff to share (e.g. iso images or other). how can i manage it?

---

### Post by anatole on 2005-11-23
[QUOTE=pirozzi]sure i have some stuff to share (e.g. iso images or other). how can i manage it?[/QUOTE]

you don't. on bittorrent, you share what you are downloading in the moment - and after you finished, it is nice (lets say expected) to share back the amount that you downloaded so your share ratio passes 1.00.
if you did not set up something for a firewall i assume everything is set properly, except that you are behind a router (and its built-in firewall). in this case, you should forward ports 6881-6889 (TCP) for proper use (at least, these are the ports most bt clients will listen on - i don't know about bittornado, you may want to check it in its settings).

---

