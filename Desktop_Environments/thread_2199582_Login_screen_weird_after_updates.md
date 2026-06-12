---
title: "Login screen weird after updates?"
date: 2014-01-14
forum: Desktop Environments
---

### Post by einstein**-7 on 2014-01-14
Just did some 600+ updates and when the login screen comes up it doesn't look like the unity greeter i had before.. It's white and has a login box in the middle kinda looks like the xfce theme. How do I get the unity greeter back?
thanks,

---

### Post by einstein**-7 on 2014-01-14
Found this and worked.

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```

---

### Post by PopsTheSailor on 2014-01-25
I have a similar problem except that I'm using Mint 16 with Cinnamon. Will the above reset it for Mint too or can someone recommend a similar process to reset the login screen?

---

