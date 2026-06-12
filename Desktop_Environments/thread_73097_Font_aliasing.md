---
title: "Font aliasing"
date: 2005-10-08
forum: Desktop Environments
---

### Post by b34r on 2005-10-08
How can i make firefox use "monospace", when a webpage wants to use "fixedsys" ?
I guess theres something to do in /etc/fonts/local.conf ... but i cant figure it out

---

### Post by khc on 2005-10-08
I _think_ this may work:
```

<alias>
  <family>fixedsys</family>
  <prefer>
    <family>monospace</family>
  </prefer>
</alias>

```

---

### Post by b34r on 2005-10-09
Yay! that did the trick
thank you

---

