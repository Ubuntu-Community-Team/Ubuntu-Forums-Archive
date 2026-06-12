---
title: "Question about NANO text editor"
date: 2009-02-23
forum: General Help
---

### Post by Krupski on 2009-02-23
Hi all,

Could someone please explain to me what the following configuration option in "/etc/nanorc" does and how to set it?

```

## The two single-column characters used to display the first characters
## of tabs and spaces.  187 in ISO 8859-1 (0000BB in Unicode) and 183 in
## ISO-8859-1 (0000B7 in Unicode) seem to be good values for these.
set whitespace "  "

```

The only information I could find using Google and the man page for nano and nanorc was [COLOR="Red"]"The two single-column characters used to display the first characters of tabs and spaces"[/COLOR] which is obviously no help!

If anyone can tell me how this works and how to set it up properly, I would greatly appreciate it.

Thanks!

-- Roger

---

### Post by geirha on 2009-02-23
It's for being able to spot whether spacing is made by tabs or spaces. If you set it to the two characters they recommend in the comment

```
set whitespace "«·"
```

And then in nano do M-P (Alt+p), it will toggle between displaying spaces and tabs normally and with those two characters. Make a file with some tabs and spaces and see what happens when you hit Alt+p.

---

### Post by Krupski on 2009-02-23
> **geirha said:**
> It's for being able to spot whether spacing is made by tabs or spaces. If you set it to the two characters they recommend in the comment

```
set whitespace "«·"
```

And then in nano do M-P (Alt+p), it will toggle between displaying spaces and tabs normally and with those two characters. Make a file with some tabs and spaces and see what happens when you hit Alt+p.

AWESOME! I didn't know I had to use Alt-p to "activate" it.

Thank you so much!!! [IMG]http://www.gunsnet.net/forums/images/smilies/Thanx.gif[/IMG]

-- Roger

---

