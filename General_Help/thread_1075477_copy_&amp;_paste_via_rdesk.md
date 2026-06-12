---
title: "copy &amp; paste via rdesk"
date: 2009-02-20
forum: General Help
---

### Post by cynoclast on 2009-02-20
I'm running Ubuntu 8.04 and I cannot get remotedesktop to allow **both** copying & pasting from my local machine into the remote desktop **and** copy & pasting within the remote desktop.

That is, if I run rdesktop with the -5 (RDP protocal v5) I'm able to copy from ubuntu to the windows machine I'm working on, but cannot copy & paste from the windows machine to itself.

If I run rdesktop **without** -5 I can copy/paste within the remote machine.  that is I can copy text from notepad to itself just fine, but I **cannot** copy/paste from my local machine to it, or back.

Is there some way to get both of these working?

---

### Post by cynoclast on 2009-02-20
I sort of fixed the problem.

Removing the Glipper (goodbye multiple clipboard entries) from my panel combined with -5 in rdesktop makes copy pasting work from Ubuntu to the the remote desktop, but the act of copy pasting from ubuntu to the remote desktop breaks copy pasting within the remote desktop.

Killing rdpclip on the remote windows box and restarting it restores remote copy pasting.....until I copy/paste from ubuntu again.

What a pain in the ***.

---

