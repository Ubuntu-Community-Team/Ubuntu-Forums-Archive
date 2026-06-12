---
title: "nmap not installing........"
date: 2009-04-06
forum: General Help
---

### Post by abhilashm86 on 2009-04-06
i don't have ubuntu 8.04 cd with me, so when i tried installing nmap,OS is asking to insert ubuntu 8.04 and try, so how to update sources list?

---

### Post by kryptikos on 2009-04-06
Sounds as if your box is still referencing the CD for installation source. To modify where she goes and looks to install from:

Click on System -> Administration -> Synaptic Package Manager

Once that opens click on: Settings -> Repositories. 

De-select the checkbox that says "Cdrom with <your version> 'name of version'"

Click "Close" then once you are returned to the main Synaptic page click the "reload" button to get synaptic to refresh itself from the online repositories. You should be able to get nmap then.

---

### Post by abhilashm86 on 2009-04-06
> **kryptikos said:**
> Sounds as if your box is still referencing the CD for installation source. To modify where she goes and looks to install from:

Click on System -> Administration -> Synaptic Package Manager

Once that opens click on: Settings -> Repositories. 

De-select the checkbox that says "Cdrom with <your version> 'name of version'"

Click "Close" then once you are returned to the main Synaptic page click the "reload" button to get synaptic to refresh itself from the online repositories. You should be to get nmap then.

ya you are right, in third party software, i unchecked which were telling cd's.........it got installed:) thanks

---

### Post by kryptikos on 2009-04-06
Happy to help :)

---

