---
title: "Where can i find a complete list of drivers for my system?"
date: 2009-02-11
forum: General Help
---

### Post by kapok on 2009-02-11
i need to find the name of my current wireless driver so i can blacklist it.

---

### Post by m_duck on 2009-02-11
If you run the following in the terminal, look at the output for your adaptor (if you have more than one), and under the "configuration" line on the output will be an entry which says driver=something.```
lshw -C network
```

---

### Post by kapok on 2009-02-11
many thanks; its up and working.

---

