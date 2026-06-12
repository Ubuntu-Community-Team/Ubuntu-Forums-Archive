---
title: "bug: gnome-panel disable function key"
date: 2008-05-21
forum: Desktop Environments
---

### Post by Phulerock on 2008-05-21
My laptop run ubuntu desktop 8.04 &#7881;86.
Sometime I have a BIG problem with CTRL, ATL, CAPLOCK, key. They are disabled. 
I thinks it may be bug of gnome-panel when I run VMware 1.05 ?!?! Because if sometime I run VMware server, this problem appear:
```
cat /var/log/messages | grep gnome-panel
May 21 16:46:53 phulerock-laptop kernel: [ 3405.113479] gnome-panel[6067]: segfault at 00000043 eip b7948275 esp bf943eb0 error 4
May 21 16:47:38 phulerock-laptop kernel: [ 3423.844390] gnome-panel[12850]: segfault at 00000043 eip b7949275 esp bff668c0 error 4
May 21 16:47:39 phulerock-laptop kernel: [ 3425.142840] gnome-panel[12929]: segfault at 00000044 eip b78ef275 esp bf98e780 error 4
May 21 16:47:41 phulerock-laptop kernel: [ 3426.427944] gnome-panel[12940]: segfault at 00000043 eip b7963275 esp bfca6290 error 4
May 21 16:50:07 phulerock-laptop kernel: [ 3464.636941] gnome-panel[12949]: segfault at 00000043 eip b7984275 esp bfd00af0 error 4

```

anyone help me

---

