---
title: "Kernels - 386/686/K7"
date: 2005-10-13
forum: Desktop Environments
---

### Post by gaz514 on 2005-10-13
I have an AMD64 processor, but I'm running the 32-bit Ubuntu (mainly for reasons of simplicity and support, but that's a whole other topic), and I noticed that there were other kernels available as well as the standard 386 one, which are 686 and K7. I assume I should install the K7 one, since I have an AMD processor, for better performance? Just thought I should check. Also, which package should I choose? linux-k7? linux-image-k7? Or is there even any point in changing the kernel?

---

### Post by Ampersand on 2005-10-13
You should see some speed increases if you use the kernel for your processor, but it's not completely necessary.

The linux-k7 package depends on the latest linux-image, making it easier to update to the latest version. It doesn't make too much difference either way.

---

