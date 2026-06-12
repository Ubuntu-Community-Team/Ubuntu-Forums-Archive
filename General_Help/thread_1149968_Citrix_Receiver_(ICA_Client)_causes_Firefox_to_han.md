---
title: "Citrix Receiver (ICA Client) causes Firefox to hang"
date: 2009-05-05
forum: General Help
---

### Post by quadra on 2009-05-05
Hi there

Recently, after some package upgrades, my Citrix client suddenly refused to work. I use it to connect to my employer's network remotely and normally it just worked like a charm.

Symptom: Client hangs, and causes Firefox [3.0.8] to hang, at about 80% in progress bar. The remote window was not yet open. No error message.

Consequence: I needed to force Firefox to quit.

I tried to downgrade Firefox to the previous version, disable extensions, delete private data and so. This did not help.

Finally, what helped was:
- Delete (rename) the firefox profile (in ~/.mozilla)
- Delete ~/.ICAclient
- Delete ~/.citrix and ~/.juniper.... if existing

Good luck!

---

### Post by And-car on 2009-07-09
This nearly worked for me but still does not connect. However I am one step on as Google no longer hangs! If you've got any more ideas I'd be grateful....!

---

