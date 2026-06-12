---
title: "Landscape for home lan use? To big or unwieldy to use?"
date: 2016-04-10
forum: Debian
---

### Post by Tadaen_Sylvermane on 2016-04-10
I have 2 laptops and one server with one virtual machine running at all times. I've flipflopped around on distros, currently my laptop has debian stable on it. I'm looking for central easy management so I can do updates and such on all machines simultaneously. Is landscape worth using (is free up to 10 computers) or it just to much to be worth it? I'm hoping I'll be adding a couple virtual machines and another laptop or desktop in the near future.

---

### Post by nerdtron on 2016-04-11
Well, Landscape is a good option. But do you really need it?  How many servers do you plan to manage? We've been managing ~100 servers and did not need additional automatic administration tools. Although we can do that, most of the needed tasks are completed by writing shell scripts and trigger it to run on all servers.

---

### Post by mastablasta on 2016-04-11
not worth it. also setup unattended updates and schedule them at the same time.

---

### Post by Bucky Ball on 2016-04-11
*Thread moved to **Debian**.*

---

### Post by lukeiamyourfather on 2016-04-11
Why move this to Debian section? The user is asking about Landscape which is a feature of Ubuntu. For the original poster, you might want to look into Salt. It's easy to setup and can be used to configure many machines at once. It lets you run commands on multiple machines very easily. It's also distribution agnostic (works on OS X and Windows too).

---

### Post by slickymaster on 2016-04-11
> **lukeiamyourfather said:**
> Why move this to Debian section? The user is asking about Landscape which is a feature of Ubuntu. <---snip--->

It was moved because the OP clearly states in his opening post that is under Debian stable.

---

### Post by Tadaen_Sylvermane on 2016-04-11
I should have specified that I would be switching to Ubuntu on my laptop had Landscape been worth it for me to use. Thank you fro replies.

---

