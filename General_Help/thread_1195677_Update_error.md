---
title: "Update error"
date: 2009-06-24
forum: General Help
---

### Post by adam321123 on 2009-06-24
I keep getting this when I try to update...



> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C0B56813051D8B58

---

### Post by adam321123 on 2009-06-24
This happened after I tried installing OpenShot Video editor and I accidentally closed terminal before It finished... tried rerunning it and it ended up removing several packages and basically with this update error... who knows what else I might of messed up

---

### Post by Soul-Sing on 2009-06-24
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C0B56813051D8B58 
```

---

### Post by adam321123 on 2009-06-24
thanks that did the trick

---

