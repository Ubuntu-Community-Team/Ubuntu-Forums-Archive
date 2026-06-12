---
title: "Show history with date"
date: 2009-02-03
forum: General Help
---

### Post by siuchi on 2009-02-03
When type history in shell, it shows your previous typed command.

How can I make it show the command together with the date and time it is typed ?

Thanks

---

### Post by dcstar on 2009-02-03
> **siuchi said:**
> When type history in shell, it shows your previous typed command.

How can I make it show the command together with the date and time it is typed ?

Thanks

You can't, it just keeps a simple list of commands.

---

### Post by KeyserSoze93 on 2009-02-04
You can set bash to date history entries. Try this:

```
HISTTIMEFORMAT="%d/%m/%y %H:%M "
```

This will not help with any commands typed prior to this, since they will just get a default time of when you turned history on, but it will log the time of any further commands.

If you want it to always log, you should probably put that somewhere in your ~/.bashrc

It's worth reading the bash man pages, they look obvious at first, but there is all sorts of useful variables and options hidden in there. I just did "man bash", and searched for history.

---

### Post by mb_webguy on 2009-02-04
As KeyserSoze93 said.  Any commands issued prior to setting HISTTIMEFORMAT will be marked with the time you set HISTTIMEFORMAT.

If you want this to be permanent, you need to add the following line to your .bashrc file:```
export HISTTIMEFORMAT="%d/%m/%y %H:%M "
```

You'll need to exit the terminal before this will take effect.

---

