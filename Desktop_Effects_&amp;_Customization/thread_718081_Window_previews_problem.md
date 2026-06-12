---
title: "Window previews problem"
date: 2008-03-07
forum: Desktop Effects &amp; Customization
---

### Post by gfl on 2008-03-07
Hi,
I have a small problem with Compiz in Ubuntu 7.10 . After installing gdesklets window previews only appear after I right click on the active window in the list . If I click on another window they disappear again. I tried uninstalling gdesklets, to no avail. Any ideas?

---

### Post by andredaflauta on 2008-03-08
Check if Widget Layer is activated. If it is, deactivate it and see if it works.

---

### Post by gfl on 2008-03-08
I tried that already - no difference, but thanks. I'm wondering if it's just that I only noticed it after trying gdesklets and there may be no connection.

---

### Post by gfl on 2008-03-10
Fixed it - I found a .gdesklets folder in my home directory. Synaptic sometimes leaves files even with the 'complete removal' option. I deleted it and on logging in again lost some panel applets - easily replaced. After rebooting everything was OK. I tried gdesklets in another user account with a default desktop and it was OK, so I guess the problem was a conflict with my settings.

---

