---
title: "The IP address reported to tracker option in rTorrent"
date: 2010-06-02
forum: Desktop Environments
---

### Post by mohtasham1983 on 2010-06-02
Hi,

I was wondering if any of rTorrent users know what The IP address reported to tracker option does in the config file? 

Can we use this option to hide our IP address from the ISP as well?

Thanks in advance

---

### Post by lovinglinux on 2010-06-03
> **mohtasham1983 said:**
> Can we use this option to hide our IP address from the ISP as well?

No. If you set the tracker to report to another IP, then other peers won't be able to request connections to you. You will still be able to download, because your client will request connections to other peers using the correct IP. So, there is no point in using that feature for what you want.

There is no such thing as hiding from your ISP.

If you are worried that what you are downloading might be illegal, then don't download it.

---

