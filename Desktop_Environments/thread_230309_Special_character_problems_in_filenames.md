---
title: "Special character problems in filenames"
date: 2006-08-05
forum: Desktop Environments
---

### Post by nightw on 2006-08-05
Hi!

I have a difficult locale/encoding/filesystem/charset problem. First: I have a simple Dapper installation. My default language is hungarian. So the output of locale says:

```

LANG=hu_HU.UTF-8
LANGUAGE=hu_HU.UTF-8
LC_CTYPE="hu_HU.UTF-8"
LC_NUMERIC="hu_HU.UTF-8"
LC_TIME="hu_HU.UTF-8"
LC_COLLATE="hu_HU.UTF-8"
LC_MONETARY="hu_HU.UTF-8"
LC_MESSAGES="hu_HU.UTF-8"
LC_PAPER="hu_HU.UTF-8"
LC_NAME="hu_HU.UTF-8"
LC_ADDRESS="hu_HU.UTF-8"
LC_TELEPHONE="hu_HU.UTF-8"
LC_MEASUREMENT="hu_HU.UTF-8"
LC_IDENTIFICATION="hu_HU.UTF-8"
LC_ALL=

```

But i have a reiser4 partition from a previous linux installation. I have a custom kernel, so it works. But when i look for some files with special chars in their name they turn to be "?"(question marks). I googled the problem and found a program called convmv. When i try to convert the files with it it says they're already utf8.
Some other info:
Reiser4 doesn not have an iocharset or nls mount option.
start_unicode and stop_unicode makes no change.
char consoles(ctrl+alt+f1 and so on) and gnome also has this problem. Nautilus even writes "Invalid Unicode" after the file name when i try to burn a file to a disc with it.
And (just) in char consoles(ctrl+alt+f1 and so on) i can't write in some of the special chars with my keyboard. Some of them are not showed correctly(for example: a fulled square instead of "&#369;").

Does anyone has any idea?

---

