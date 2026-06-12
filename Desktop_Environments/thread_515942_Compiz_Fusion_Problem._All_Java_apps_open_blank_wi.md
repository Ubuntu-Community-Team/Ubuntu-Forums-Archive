---
title: "Compiz Fusion Problem. All Java apps open blank window"
date: 2007-08-02
forum: Desktop Environments
---

### Post by noneedforwindows on 2007-08-02
I am loving these Compiz effects they are awesome. I just installed Limewire with a .deb file that installed dependencies aswell. When it was done the install along with installing java, Limewire is just a blank screen of white. I am using a xgl session with fglrx drivers. Ive searched around the forums and I didn't find a straight answer to this question. Thanks in advance.

---

### Post by Chudilo on 2007-08-02
Yuo need Java 6 update 1 or later to get Compiz support

---

### Post by jpolanco on 2007-08-02
Try putting this at the last line of your /etc/profile :

```

export AWT_TOOLKIT=MToolkit
```

---

