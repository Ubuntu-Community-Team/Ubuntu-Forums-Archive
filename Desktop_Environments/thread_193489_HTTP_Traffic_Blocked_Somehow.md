---
title: "HTTP Traffic Blocked Somehow?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by T-Dizzle on 2006-06-10
Strange thing happening to me...HTTP traffic is somehow being blocked, but I can't figure out why.

Everything works fine until about 1 minute or so after booting.  Then, everything works except Web browsing. Gaim, DNS resolution, and ping all work, but I can't browse anywhere except Google, for some reason.  Trying to surf using wget tells me the HTTP request was sent, but no reply is ever received.

However, I can freely surf on my Mac, which is behind the same router and on the same subnet as my Ubuntu box.

I have firestarter installed and running, but outbound policy is permissive with no blacklisting.  Turning off the firewall 

This problem happened to me a couple nights ago, but I was able to fix it after rebooting.  Now the problem seems persistent and I'm not sure what to do.

Can anyone tell me what I'm doing wrong?

T./

---

### Post by alamba on 2006-06-10
What happens when you turn off the firewall? Do you have a proxy setup on your network patch which u're using in the Mac but not on Ubuntu? Can you run a sniffer like tethereal and check what's going on?

A

---

