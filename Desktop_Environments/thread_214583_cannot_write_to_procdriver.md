---
title: "cannot write to /proc/driver"
date: 2006-07-12
forum: Desktop Environments
---

### Post by sup on 2006-07-12
I use notebook "Prestigio 157" and I must use acerhk module for enabling some additional keys next to regular keyboard. From  my searching, I found that I also need to pass "1" to /proc/driver/acerhk/wirelessled when I want suspend to ram work.

Now, however,  
```
sudo -s
echo >1 /proc/driver/acerhk/wirelessled
```
does not work (it does not give anythyng back, no message, no error) - when I do
```
 cat /proc/driver/acerhk/wirelessled
```
nothing happens.

Any idea why is that so? Is proc directory mount read-only? file premissions allowev only write, no reading, but when I chmod +r it, it didnot helped...

---

