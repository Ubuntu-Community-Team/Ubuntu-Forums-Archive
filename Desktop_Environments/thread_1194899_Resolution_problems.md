---
title: "Resolution problems"
date: 2009-06-23
forum: Desktop Environments
---

### Post by rocker.praneeth on 2009-06-23
I have problem for me there is no resolution after 800x600 i cannot increase my resolution i cnnot enable visual effects also please take out me from this problem

---

### Post by prshah on 2009-06-23
> **rocker.praneeth said:**
> I have problem for me there is no resolution after 800x600 i cannot increase my resolution i cnnot enable visual effects also please take out me from this problem

we need more information for example your system configuration video card ubuntu version what you have already done and i also suggest you to use proper punctuation because it is very confusing if you run everything into one long sentence and especially more so if you do not use punctuation please take the time to frame the question properly just the same way as others take time to frame answers properly.

To get information about your system, open a terminal (Applications-Accessories-Terminal), and give the commands ```
lspci | grep -i -E graphics\|vga
cat /var/log/Xorg.0.log | grep -i driver

```

---

