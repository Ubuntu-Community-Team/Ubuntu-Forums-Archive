---
title: "what tool i can use to look at very big binary files?"
date: 2009-03-17
forum: General Help
---

### Post by q.dinar on 2009-03-17
hello.
what tool i can use to look at very big binary files?
i have tried cat and tail. they are not right tools. as i remember and have just checked, cat shows whole file and tail can show only last n lines or last n bytes.
i mean just looking like in text editor or hex editor. but i do not want hex view like in hex editor. (may be there is option in some hex editor to turn off hex view.)
but many text editors i have seen cannot handle such big files correct way. they load big file into memory and it looks like going into swap. i just need to view through file, there are functions to read particular byte of file, so it should not be loaded wholly.
gedit does not open binary files at all and does not scroll text files with long lines correctly.

---

### Post by sdennie on 2009-03-17
Try:

```

od file | more

```

Check the od man page for different display options.

---

### Post by Dr Small on 2009-03-17
Vim

---

### Post by HermanAB on 2009-03-17
hexedit

Cheers,

Herman

---

