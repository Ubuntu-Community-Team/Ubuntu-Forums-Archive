---
title: "No internet connection after update"
date: 2009-02-01
forum: General Help
---

### Post by txtinman on 2009-02-01
I recently did a software update at the suggestion of the package manager. I think there were about 60 packages that updated and I don't remember what they all were. I know I did not update the kernel. After the update I lost my internet connection. I have another computer attached to the router that still has it's connection. Since the connection worked right up to the upgrade, I doubt that the hardware has failed. How can I troubleshoot this problem?

I found a thread that suggested the /etc/network/interfaces file might be the culprit. I deleted all references to eth0 and then manually entered them again. I now have my internet connection back. Why this worked, I have no idea.

---

### Post by bumanie on 2009-02-01
Is it a wired connection to an ethernet port or is it a wi-fi connection that has been lost? If wi-fi, what type of wi-fi card is it?

---

### Post by txtinman on 2009-02-01
> **bumanie said:**
> Is it a wired connection to an ethernet port or is it a wi-fi connection that has been lost? If wi-fi, what type of wi-fi card is it?
It is a wired connection from a linksys router to a realtek card.

---

