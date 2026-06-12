---
title: "how do i get console history back?"
date: 2005-10-11
forum: Desktop Environments
---

### Post by sal on 2005-10-11
i used the ubuntuguide "disable history listing in Console mode" set up [http://ubuntuguide.org/#disablehistorylistingconsole](http://ubuntuguide.org/#disablehistorylistingconsole) and now want to be able to use the history again.
what would i have to do to get the console history back?
thanks.

in case its needed,
im running kubuntu breezy 5.10 with kde 3.5B

---

### Post by bored2k on 2005-10-11
```
chmod 600 $HOME/.bash_history
```Try that.

---

### Post by sal on 2005-10-11
[QUOTE=bored2k]```
chmod 600 $HOME/.bash_history
```Try that.[/QUOTE]

thanks.

---

