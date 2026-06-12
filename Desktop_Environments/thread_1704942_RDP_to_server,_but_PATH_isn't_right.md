---
title: "RDP to server, but PATH isn't right"
date: 2011-03-11
forum: Desktop Environments
---

### Post by ScottEChapman on 2011-03-11
So, I noticed something a bit odd...

I am running 10.04 LTS and put the ubuntu desktop on it, and installed XRDP server so I can remote desktop to it from my windows client.

Works like a champ. With one exception.

When it starts up the PATH it has isn't right. For example, it doesn't contain any of the sbin components that would allow synaptic package manager to do it's thing (or more specifically it can't find ldconfig etc...)

I checked and made sure that /etc/environment has the right thing in it, but that apparently isn't right.

Any ideas?

---

