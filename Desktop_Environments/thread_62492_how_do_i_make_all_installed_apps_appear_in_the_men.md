---
title: "how do i make all installed apps appear in the menu?"
date: 2005-09-04
forum: Desktop Environments
---

### Post by Digitallysick on 2005-09-04
I just installed kubuntu, gimp wasn't in my menu, so i went to do an apt-get install gimp , and it said it was already installed , so i opened the konsole and i was able to type gimp and bring it up. So my question is , any way to automaticlly put all apps into the menu?? I could have alot of other things install i dont know about?

---

### Post by f1dave on 2005-09-04
Once you restart KDE, gimp /should/ appear in your menu anyhow.

If for some strange reason it does not, add it manually by right-clicking the kmenu and selecting "edit the kmenu".

---

### Post by Takis on 2005-09-05
By default, the GIMP tries to add an entry to the 'Graphics' submenu. If that doesn't exist (for example, you've renamed it) it won't add itself anywhere.

---

### Post by GeneralZod on 2005-09-06
As said, it *should* be there.  Try running 

```

kappfinder

```

just in case, though.

---

