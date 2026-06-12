---
title: "Turning off desktop effects via SSH"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by ibbuntu on 2007-04-30
Is there a way to turn of desktop effects at the command line via SSH? I can't VNC to my home computer when it has desktop effects turned on and I believe the only current solution is to turn them of, but I forgot to do this when I left home this morning.

---

### Post by Rashid584 on 2007-05-01
i assume you can just killall compiz/beryl right?

-Rashid

---

### Post by rolf-c on 2007-05-01
Also I suppose the persistent setting lives somewhere in ~/.gconf, but modifying anything in there will likely require an X restart...a good option from Rashid above is killall.  That certainly gets around having to restart X.

---

### Post by smooth_b on 2007-05-02
You could  use NX instead of VNC. NX is much faster than VNC. Check it out at [http://nomachine.com](http://nomachine.com)

---

### Post by ibbuntu on 2007-05-03
> **smooth_b said:**
> You could  use NX instead of VNC. NX is much faster than VNC. Check it out at [http://nomachine.com](http://nomachine.com)

I have NX installed and have used it a bit, but I find that it's quite unstable with my system. It crashes after about 5 minutes of use and then I am unable to log in again, so I've had to fall back on VNC.

Thanks for the other replies, I have remembered to turn off desktop effects now, but the next time I forget I will try out your suggestions.

---

