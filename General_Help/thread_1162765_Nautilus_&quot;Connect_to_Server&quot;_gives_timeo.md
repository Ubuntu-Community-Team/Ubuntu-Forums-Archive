---
title: "Nautilus &quot;Connect to Server&quot; gives timeout error"
date: 2009-05-18
forum: General Help
---

### Post by davidmigl on 2009-05-18
Hi,

I have 2 computers on a local network, satellos (the server) and davidmigl (client). I just reinstalled linux on satellos b/c I needed to replace the hard drive. Previously, when I went to Places -> Connect to Server and typed in "satellos" and my username, it would connect via ssh just fine. Now it gives me a timeout error.

I can ssh and vnc into the machine just fine.

My ssh is griping at me because the host key has changed - I'm pretty sure satellos has a new ip address since the os was reinstalled. Could this have anything to do with this?


Thanks!
David

---

### Post by davidmigl on 2009-05-18
As I suspected, my client computer had an outdated entry for satellos in its known hosts files. The solution was to go to [home folder]/.ssh and clear out the known_hosts file so it could start from scratch. Now it works just fine.

---

