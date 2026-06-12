---
title: "Can I make a set of nested folder via command line?"
date: 2009-06-16
forum: General Help
---

### Post by Mycle on 2009-06-16
Please would anyone be kind enough to help me out with a couple of newbie questions?

If I want to make a set of nested folders inside my "Home" folder, such as:

DocLib/Computer/OS/Linux/Ubuntu/Server/

Can I do it via the command line by typing out the full path and make them all in one hit?

In Windows I use the keystrokes: Alt+F-W-F to make a new folder. Is there a keystroke equivalent in Ubuntu?
TIA
Mycle

---

### Post by leandromartinez98 on 2009-06-16
```

cd ~
mkdir -p DocLib/Computer/OS/Linux/Ubuntu/Server/

```

Edit: The keystroke is Shift-Control-N (in the file browser, Nautilus)

Edit2: Added the "-p" to the command is correct and do not confuses other people.

---

### Post by boof1988 on 2009-06-16
You can use the option "*-p*" so *mkdir* will create the nested directories.

Example...
```

mkdir -p ~/DocLib/Computer/OS/Linux/Ubuntu/Server/

```

...will create any non-existing (nested) directories.

Also see...
```

man mkdir

```

---

### Post by leandromartinez98 on 2009-06-16
Yes, boof1988 is right, you need the "-p". I had it as default (as an
alias on my .bashrc and forgot it).

---

### Post by Mycle on 2009-06-17
Thanks ever so guys! 
That was a big help.
--
Regards,
Mycle

---

