---
title: "Can't connect to MSN with Pidgin"
date: 2009-06-03
forum: General Help
---

### Post by NCLI on 2009-06-03
I've been using Pidgin as my IM client for a long time, but I can't connect to my MSN account any more. 

Empathy connects just fine, only Pidgin can't. I get this message:> Your MSN buddy list is temporarily unavailable. Please wait and try again.

---

### Post by Tibuda on 2009-06-03
Try using the alternate WLM protocol. Install the [msn-pecan]("apt:msn-pecan") package from Synaptic, disable your current MSN account in Pidgin and create a new account using the WLM protocol.

---

### Post by NCLI on 2009-06-03
> **danielrmt said:**
> Try using the alternate WLM protocol. Install the [msn-pecan]("apt:msn-pecan") package from Synaptic, disable your current MSN account in Pidgin and create a new account using the WLM protocol.

Great, it works!!

Could you tell me what the difference is between the two protocols?

---

### Post by Tibuda on 2009-06-03
This is from the package description in Synaptic:
[QUOTE="Synaptic"]Compared to Pidgin's official MSN plug-in:
 * Faster log-in
 * Fewer connection issues
 * Experimental direct connection support (fast file transfers)
 * Server-side storage for display names (private alias)
 * Support for handwritten messages (read-only)
 * Support for voice clips (receive-only)
 * Support for Plus! sounds (receive-only)
 * Option to hide Plus! tags

Other features:
 * Support for personal status messages
 * Support for offline messaging (read-only)
 * Send custom emoticons (Pidgin >= 2.5)[/QUOTE]

---

### Post by Flywaver on 2009-06-14
> **danielrmt said:**
> Try using the alternate WLM protocol. Install the [msn-pecan]("apt:msn-pecan") package from Synaptic, disable your current MSN account in Pidgin and create a new account using the WLM protocol.

Did this and it seems I am connected to MSN but there are no buddies, as if I had no contacts lol

---

