---
title: "amarok + arts"
date: 2005-10-15
forum: Desktop Environments
---

### Post by f1dave on 2005-10-15
hey everyone,

recently upgraded from hoary (kde 3.4.2) to breezy (3.5 beta1). It's all good, except amaroK now refuses to use arts- or anything, really :S This is the error:

KLibLoader could not load the plugin:
libamarok_artsengine_plugin
Error message:
/usr/lib/libamarokarts.so: undefined symbol: _ZTv0_n32_N4Arts16SynthModule_stub11autoSuspendEv

Any ideas?

Edit: i should point out juK works fine, as do system sounds.

---

### Post by daller on 2005-11-15
Try using the osssink as the output-plugin

---

### Post by f1dave on 2005-11-15
I should have said, it's fine now... I'm using bleeding-edge SVN versions :P

---

