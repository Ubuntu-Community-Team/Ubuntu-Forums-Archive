---
title: "X-server...dead"
date: 2005-04-02
forum: Desktop Environments
---

### Post by StrikeRTM on 2005-04-02
I was trying to install ATI draivers on my machine. Everything went good, just the x-server config didn't, I messed up somethng and I have no idea how to bring up config from comand-line... ](*,)  :-k

How do I bring up the config?

---

### Post by fdoving on 2005-04-02
try to run this command:
```

sudo dpkg-reconfigure xserver-xorg

```

God luck.

---

### Post by dcraven on 2005-04-02
[QUOTE=StrikeRTM]
How do I bring up the config?[/QUOTE]

If by "bring up the config" you mean in a text editor, then the following command will work. Feel free to substitiute nano for your favorite editor.
```

# nano /etc/X11/xorg.conf

```

HTH,
~djc

---

