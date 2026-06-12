---
title: "Customize Start Up Text"
date: 2008-07-24
forum: Desktop Environments
---

### Post by th3gh05t on 2008-07-24
Hi-

I searched around these forums, but couldn't find anything related to this.

After the Ubuntu screen with the loading bar, it scrolls some text loading up modules or whatever. On my screen, this text is all ugly (Courier New), off-centered, etc.

How do we go about changing this text? Also, is there a way to scroll that text underneath the loading bar page? Instead of have it advance to a second screen?

Thanks for your help and time!

Derek

---

### Post by pauper on 2008-07-24
To choose another font run:

```
sudo dpkg-reconfigure console-setup
```

Read relevant documentation about setting resolution here:

[http://www.mjmwired.net/kernel/Documentation/fb/vesafb.txt](http://www.mjmwired.net/kernel/Documentation/fb/vesafb.txt)
[http://www.mjmwired.net/kernel/Documentation/svga.txt](http://www.mjmwired.net/kernel/Documentation/svga.txt)

---

### Post by th3gh05t on 2008-07-24
Thanks! I'll give it a shot!

---

