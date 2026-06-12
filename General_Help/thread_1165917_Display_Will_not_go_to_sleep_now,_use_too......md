---
title: "Display Will not go to sleep now, use too....."
date: 2009-05-21
forum: General Help
---

### Post by jenkins_t on 2009-05-21
Hello all,
I have a pretty much default ubuntu install on a built x86 desktop pc. When I first installed, the display would go to sleep, but not the OS, as defined. But now every morning the display is always alive! I am going to burn up my flat panel soon, any suggestions?

---

### Post by Bindsa on 2009-05-21
First of all, your flat panel will not burn away, they are designed to cope with these circumstances. Secondly, do you have a swap area on your system? If not, then make one and try re-enabling the sleep mode.

---

### Post by jenkins_t on 2009-05-21
Swap is on. Also, once again, my display used to turn off, now it dont


$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	851404	22680	-1

---

### Post by jenkins_t on 2009-05-22
Fixed, Found 2 powermanagement services enabled. Disabled one and OK. Maybe one got turned on during update?

[IMG]http://vhbc.net/services.png[/IMG]

---

