---
title: "XMMS broke when I upgraded to kernel 2.6.12-10"
date: 2005-12-15
forum: General Help
---

### Post by HoneyGutClusters on 2005-12-15
Just as the title says. I can no longer execute XMMS. When I try to run it from the main menu, it does nothing. I try to lauch it from the terminal, and it just returns to the prompt.

This started happening after synaptic installed the 2.6.12-10 kernel and I rebooted. I also tried removing XMMS with synaptic and installing the package from packages.debian.org with no luck.

any ideas?

---

### Post by Perfect Storm on 2005-12-15
Have you tried uninstall Xmms completly via synaptic package manager and removed .xmms from your home directory? And then reinstall xmms from synaptic?

---

### Post by HoneyGutClusters on 2005-12-15
tried all that except the removing the .xmms folder. I'll try that now.

---

### Post by HoneyGutClusters on 2005-12-15
When I did a complete uninstall in Synaptic, it removed the .xmms folder. However. I was able to fix this problem by rm -rf'ing  /tmp/xmms_user.0

thank you for your help.

---

