---
title: "E:dpkg problems"
date: 2008-02-15
forum: Dell  Ubuntu Support
---

### Post by Anarcyn on 2008-02-15
I have a error whenever i try to use the Synaptic Package Manager i gives me a message that says "E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" but when i do that in the terminal it just says no dpkg command found please help

---

### Post by jan quark on 2008-02-17
try this
```

sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

