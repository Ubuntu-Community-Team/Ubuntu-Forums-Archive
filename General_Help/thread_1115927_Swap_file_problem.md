---
title: "Swap file problem"
date: 2009-04-04
forum: General Help
---

### Post by gauravforyouall on 2009-04-04
Hey while dealing with my hibernate problem
i tried creating swaps and reading others
i found this
when i do
cat /proc/swaps
output is

Filename		Type		Size	Used	Priority
/dev/ramzswap0          partition	385848	0	100
/dev/sda8               partition	1622524	0	-1

even i delete /dev/ramzswap0 it doesnt matter
i changed priority of sda8 in /etc/fstab again doesntseems to help

if i delete ramzswap0 and hibernate my pc goes but when i turn it on it boots again and that ramzswap0 appears from no where please help

---

