---
title: "pap-secrets"
date: 2005-06-15
forum: Desktop Environments
---

### Post by coolclassic on 2005-06-15
Having succesfully got my sagem fast 800 modem up and running. I found that on restart my pap-secrets gets rewritten to its original default setting this the causes my connection to fail at startadsl. Haw do I keep the edited pap-secrets so it does not revert to default.

---

### Post by alastair on 2005-06-15
That file should not be rewritten - what might be doing that?

You could just make it read-only i.e.

sudo chmod 400 /etc/ppp/pap-secrets

But something is wrong elsewhere.

---

