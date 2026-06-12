---
title: "No Gmailwatcher notification in messaging menu"
date: 2012-10-18
forum: Desktop Environments
---

### Post by rpk94 on 2012-10-18
I just made a fresh 12.10 install. I installed gmailwatcher and set it up. When I get an email, it notifies me, but the messaging menu indicator does not turn blue. How do I get this functionality back?

---

### Post by emdeem on 2012-10-18
Good question.  gm-notify also seems broken in 12.10.  Are there any Unity gmail indicators that work?

---

### Post by ajgreeny on 2012-10-18
> **emdeem said:**
> Good question.  gm-notify also seems broken in 12.10.  Are there any Unity gmail indicators that work?
Any idea if that is that just in unity or if it is it a general 12.10 problem?

---

### Post by emdeem on 2012-10-18
> **ajgreeny said:**
> Any idea if that is that just in unity or if it is it a general 12.10 problem?

I haven't tested it with others, but I believe it's due to a Unity API change.

---

### Post by markbl on 2012-10-18
> **emdeem said:**
> I haven't tested it with others, but I believe it's due to a Unity API change.

AFAIK, Canonical introduced a new libindicator API with Unity (Ubuntu 11.10), completely incompatible with everything else and now in their infinite wisdom they have changed it all again with a new messaging menu api. The previous api is not supported anymore. There has been little information provided about the change or the new api, and good luck to any developer trying to find documentation on the new api.

---

### Post by emdeem on 2012-10-24
unity-mail seems to work well with Quantal.  The only thing it's missing when compared to gm-notify is the ability to play a sound.

---

