---
title: "how to share a keyboard and mouse with OSX?"
date: 2023-01-30
forum: Desktop Environments
---

### Post by dwater on 2023-01-30
I used to do this with linux and irix systems back when I worked at sgi back in the noughties...but I can't find a solution today.
Can someone tell me what the solution is these days?

Ubuntu 22.10 and OSX 13.1

---

### Post by TheFu on 2023-01-30
I suspect using a "KVM switch" isn't the answer you seek?  They are relatively cheap these days, but USB switches are a pain, since they aren't instantaneous like PS2 switching was/is.

If you don't care about video, that would simplify stuff, since displayport KVMs are much more expensive than simple HDMI KVM switches.  Amazon has 50 models for your consideration.  I have a 4-port 4K HDMI KVM switch with USB switching (keyboard/mouse), audio switching and storage switching ... though I have ZERO plans/use for the audio or storage switching that's included. It was about $130.  2-port KVM switches are pretty cheap.

---

### Post by ActionParsnip on 2023-01-30
Synergy is decent. You setup the layout of the screens then when you move the mouse from one side of the screen it appears on the other system. Very cool.

---

### Post by TheFu on 2023-01-30
Thought synergy went proprietary last decade?

---

### Post by ActionParsnip on 2023-01-30
> **TheFu said:**
> Thought synergy went proprietary last decade?

Not sure. If it works then cool. Didn't see a requirement for open source / proprietaryness so suggested it

---

### Post by dwater on 2023-01-31
> **TheFu said:**
> I suspect using a "KVM switch" isn't the answer you seek?  They are relatively cheap these days, but USB switches are a pain, since they aren't instantaneous like PS2 switching was/is.

If you don't care about video, that would simplify stuff, since displayport KVMs are much more expensive than simple HDMI KVM switches.  Amazon has 50 models for your consideration.  I have a 4-port 4K HDMI KVM switch with USB switching (keyboard/mouse), audio switching and storage switching ... though I have ZERO plans/use for the audio or storage switching that's included. It was about $130.  2-port KVM switches are pretty cheap.

Yeah, I wasn't really thinking about hardware. We never used to need hardware. I guess it's worth bearing in mind, depending on how much of a pita it becomes, but not at this point. Thanks though.

---

### Post by dwater on 2023-01-31
> **ActionParsnip said:**
> Not sure. If it works then cool. Didn't see a requirement for open source / proprietaryness so suggested it

I noticed synergy. The name rings a bell, and I wonder if that was one of the options available, way back when.

I'm not especially interested in it being open source or care if it is proprietary, but I do want it to be free (of cost), like it used to be. It seems like synergy doesn't have such an option, not even for private/personal use.

Having said that, and looking more closely, it seems like it is a $29 one-time payment. There's no free frial (except for the Business version, which is a subscription), but there is a 30 day "guaranteed" refund.
...so, maybe it's worth a try.

I'm sure there used to be something that was completely free. Perhaps it wasn't OSX back then, or required us to run an X-Server on OSX...it's been too long.

---

### Post by TheFu on 2023-01-31
synergy was free - 20 yrs ago.

---

### Post by dwater on 2023-01-31
> **TheFu said:**
> synergy was free - 20 yrs ago.

Yeah, that corresponds with when I was trying this sort of thing.

---

### Post by j96hook on 2023-02-11
Barrier is an opensource alternative to synergy that works pretty well. Works best when both devices are connected to the network via ethernet. Wifi can get a bit laggy sometimes.

---

### Post by dwater on 2023-02-12
Perfect - seems to work nicely - thanks!

---

