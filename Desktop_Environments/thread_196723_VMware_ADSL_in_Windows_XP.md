---
title: "VMware ADSL in Windows XP"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Admiral Valdemar on 2006-06-14
I've finally got XP Home Edition installed on VMware Server, but I'm having problems connecting to the Internet through it. My ADSL connection is fine in Ubuntu, but how do I get the VM of XP to share it and also access the web etc.?

---

### Post by patrickfromspain on 2006-06-14
you can do a bridget internet conection, so that vmware uses the same IP ubuntu has. Anyway, this should rather be in the vmware forums.

---

### Post by Admiral Valdemar on 2006-06-14
Ah, missed the dedicated forum for this topic, my bad. How do you go about getting the connection seen by XP? The bridge connection option is checked in VMware, though I'm unsure how I set this up in XP.

---

### Post by Admiral Valdemar on 2006-06-14
So, any takers on explaining this to me? Anyone? I really do hate networking sometimes. *grumble*

---

### Post by Computeruser on 2006-06-14
If you hate networking, you should be using XP Pro. It just works. 

However:
1. To use Bridged Networking, your host machine must be behind a NAT-based router so the VM can get a different IP.
2. If this is not the case, try NAT. I use Bridged on my Desktop, and NAT on my laptop (both work). Try NAT and XP (even Home) should see the internet right away.

---

