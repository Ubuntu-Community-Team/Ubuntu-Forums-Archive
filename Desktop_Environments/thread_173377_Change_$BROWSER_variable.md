---
title: "Change $BROWSER variable"
date: 2006-05-10
forum: Desktop Environments
---

### Post by peterthebike on 2006-05-10
If I echo $BROWSER it is set to "/usr/bin/opera" how can I change it please?

I know System>Preferences>Preferred Applications>Web Browser  does not amend it and I have also checked .bashrc.

Thanks

---

### Post by cgjones on 2006-05-10
You might be able to set it in /etc/profile (I'm not at my Ubuntu machine, so I can't verify this)

---

### Post by bswilson on 2006-05-10
```
export BROWSER=/usr/bin/your-browser
```

That should fix you up.

---

### Post by peterthebike on 2006-05-10
[QUOTE=cgjones]You might be able to set it in /etc/profile (I'm not at my Ubuntu machine, so I can't verify this)[/QUOTE]

Tried it, but it doesn't change it on my system. Thanks.

---

### Post by peterthebike on 2006-05-10
[QUOTE=bswilson]```
export BROWSER=/usr/bin/your-browser
```

That should fix you up.[/QUOTE]

It is only temporary though. Reboot and it is reset. Thanks.

---

### Post by cgjones on 2006-05-10
In your .bash_profile, set the following:
```

BROWSER=/the/browser/you/want
export BROWSER

```

---

### Post by peterthebike on 2006-05-10
[QUOTE=cgjones]In your .bash_profile, set the following:
```

BROWSER=/the/browser/you/want
export BROWSER

```[/QUOTE]

That fixed it thanks! (although as I look again at your posting you did not suggest .bashrc :oops:)

---

### Post by cgjones on 2006-05-10
When I read your original post, I didn't catch that you were looking in .bashrc. User's environment variables normally go in .bash_profile, and aliases and such go in .bashrc. Although not all distro's follow that guideline.

---

### Post by _simon_ on 2006-06-13
I don't seem to have .bash_profile, where is this normally located?

---

