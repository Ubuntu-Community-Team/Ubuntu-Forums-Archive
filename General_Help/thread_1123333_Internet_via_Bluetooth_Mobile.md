---
title: "Internet via Bluetooth Mobile ??"
date: 2009-04-12
forum: General Help
---

### Post by Tom_T on 2009-04-12
Hi

I have a Nokia N95 8GB and would like know if it's possible possible to use that as a Bluetooth Modem from Jaunty ?

Thanks :)

---

### Post by Tom_T on 2009-04-12
I've been playing with BlueMan that suggests it will allow this.

But I can't get a serial connection to my mobile (N95 8GB)

Any ideas ??
I'm running Jaunty 9.04.

Thanks:)

---

### Post by walmis on 2009-04-12
NetworkManager in Jaunty changed it's modem detection strategy, so that broke DUN support in blueman 1.02. No worries, it's fixed in blueman SVN and version 1.1 is soon to be released.

[https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/269329](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/269329)

---

### Post by Tom_T on 2009-04-14
Where do I download the SVN and how do I install it ?
Thanks

---

