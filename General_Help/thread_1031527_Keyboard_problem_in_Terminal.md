---
title: "Keyboard problem in Terminal"
date: 2009-01-05
forum: General Help
---

### Post by gldearman on 2009-01-05
Hi,

I'm using Intrepid.  One user (my wife) is having some trouble with Gnome Terminal.  Certain keys on the keyboard behave strangely when she uses Terminal.  For example, the <Tab> key does not autocomplete; it seems to, instead, enter a number of spaces.  The <ArrowUp> and <ArrowDown> keys do not scroll through the history; instead, they enter what appear to be gibberish characters.  For example, <ArrowUp> enters the characters 

```
^[[A
```

Terminal works fine for me, even if I launch it from her account and then use the su command to switch to my username.

Is there a way to reset her terminal configuration to the default?  Or copy mine to her account?  Or any other way to fix this problem?

Thanks.

---

### Post by Peter09 on 2009-01-05
Have you enabled the menu bar at the top of the terminal?

---

### Post by gldearman on 2009-01-05
Yes, I have.

I have also located the cause of the strange behavior.

The set command reveals that she is using /bin/sh, which I think is the dash shell.  I am still using /bin/bash as my default shell.  Somehow, when Ubuntu changed the default shell from bash to dash, my account, but not hers, was unaffected.

So, does anyone know how to change the default shell for a user?

Thanks

---

