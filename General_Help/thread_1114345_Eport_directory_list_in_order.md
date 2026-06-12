---
title: "Eport directory list in order?"
date: 2009-04-02
forum: General Help
---

### Post by Shampyon on 2009-04-02
I'd like to export the directory/file list for my Music folder so I can always refer to it if I ever have a problem and have to replace my music. I can see the list in perfect order using *[FONT="Courier New"]ls -R /path/to/directory/[/FONT]*, but if I try to copy and paste it into a text editor or word processor the file names are out of order.

[_[COLOR="Blue"]Screenshot from terminal[/COLOR]_]("http://img55.imageshack.us/img55/114/shell.png")

[_[COLOR="Blue"]Screenshot from Abiword[/COLOR]_]("http://img55.imageshack.us/img55/4639/abiword.png")

Is there a way to export the directory list while keeping the file names in order?

---

### Post by mister_pink on 2009-04-02
Try:
```

ls -R /path/to/directory/ > textfile

```
And it will automatically be written to the textfile instead of the screen. (if you want to look it up, this is known as output redirection or piping).

---

### Post by Shampyon on 2009-04-02
Perfect! Thank you!

---

