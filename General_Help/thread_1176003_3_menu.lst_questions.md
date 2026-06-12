---
title: "3 menu.lst questions"
date: 2009-06-01
forum: General Help
---

### Post by rock4christ on 2009-06-01
1. I see in a lot of speedup guides suggesting changing the "ro quiet splash" on the kernel line to "ro", but wouldn't "ro quiet" be quicker, due to not printing the excess stuff to the screen. 

2. does removing the quiet item under initrd do much speed wise? what exactly does removing it 'unquiet'?

3. I can safely remove 
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```

right?

---

### Post by colau on 2009-06-01
> **rock4christ said:**
> 1. I see in a lot of speedup guides suggesting changing the "ro quiet splash" on the kernel line to "ro", but wouldn't "ro quiet" be quicker, due to not printing the excess stuff to the screen. 

2. does removing the quiet item under initrd do much speed wise? what exactly does removing it 'unquiet'?

3. I can safely remove 
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```

right?

It may be quicker.
```

3. I can safely remove 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```
You can remove those lines.

---

### Post by rock4christ on 2009-06-01
I was just wandering if anyone knew for sure if it was quicker, or if it was removed as well for a reason

---

### Post by x33a on 2009-06-01
yes, i use the ro quiet option, and it seems a bit quicker, as only the more important stuff is verbosed. plus, it is easier to read what's going on the screen.

---

### Post by michy99 on 2009-06-01
You should probably leave this line:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by rock4christ on 2009-06-01
ok. thanks!

---

### Post by mcduck on 2009-06-02
> **rock4christ said:**
> 1. I see in a lot of speedup guides suggesting changing the "ro quiet splash" on the kernel line to "ro", but wouldn't "ro quiet" be quicker, due to not printing the excess stuff to the screen. 

2. does removing the quiet item under initrd do much speed wise? what exactly does removing it 'unquiet'?

3. I can safely remove 
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```

right?

Last time I tested it, the difference in boot speed between splash and no splash was less than a second. Although the text boot has a lot more going on, which makes it *feel like* it would be quicker. So it's mainly a psychological thing, when there's lots of things happening people feel that things are progressing quicker.

Removing the extra lines from menu.lst won't have any effect on your boot speed. That will only make your menu.lst file harder to read. IF you still choose to remove those, you should at least leave the "### END DEBIAN AUTOMAGIC KERNELS LIST" untouched.

And then quick reference for the quiet & splash options, and what they do:
-quiet splash: graphical boot, no text
-splash: graphical boot with text
-quiet: normal text boot
-(nothing): verbose text boot, same as in the recovery mode.

---

