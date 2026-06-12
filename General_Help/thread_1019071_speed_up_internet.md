---
title: "speed up internet?"
date: 2008-12-22
forum: General Help
---

### Post by Howitzer777 on 2008-12-22
Ok, i love ubuntu but the internet is killing me. its way slower than windows. any tips on how to speed this up? i'm already using swiftfox but still slow.

---

### Post by Hangwire on 2008-12-22
sudo gedit /etc/modprobe.d/aliases

alias net-pf-10 off

Reboot. The internet should be much faster now.

This solution disables the newer internet protocol that is used to resolve newer internet addresses. The link given by the reply above gives more info on this topic.

You can also watch this: the guy explains it better.
[http://www.youtube.com/watch?v=Sd8nHsUevAY](http://www.youtube.com/watch?v=Sd8nHsUevAY)

Its the same for Ubuntu 8.04 and 8.10

---

