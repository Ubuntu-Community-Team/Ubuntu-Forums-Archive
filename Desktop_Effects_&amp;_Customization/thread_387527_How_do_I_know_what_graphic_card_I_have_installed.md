---
title: "How do I know what graphic card I have installed?"
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by Ederico on 2007-03-18
Hello, I would like to attempt the installation of Beryl, but in order to even attempt to I would like to know how can I know what type of graphic card and specifications do I have. Can anyone help?

Thanks for any help granted.

---

### Post by taurus on 2007-03-18
This little command from a terminal will tell you what graphic card you have on your machine.

```
lspci
```

---

### Post by kvonb on 2007-03-18
Open a terminal, and type the following:

```
lspci | grep VGA
```

Regards, KEv :)

---

### Post by Lord Illidan on 2007-03-18
type in ```
lspci | grep VGA
``` in the terminal

EDIT : beaten to it..

---

### Post by PriceChild on 2007-03-18
Please don't try Beryl. Its not for beginners and is unstable software. It WILL break on you.

---

