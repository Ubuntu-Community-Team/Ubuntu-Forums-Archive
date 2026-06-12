---
title: "Panel items no longer available (under Dapper Drake)"
date: 2006-08-02
forum: Desktop Environments
---

### Post by jp.stacey on 2006-08-02
Hi,

after having rsync'ed my home directories from an old Debian machine to a new Ubuntu machine I kept getting the error popup described in this thread:

[http://ubuntuforums.org/showthread.php?t=8468]("http://ubuntuforums.org/showthread.php?t=8468")

I'm running Dapper Drake on this new machine, although that thread (now closed) was for a warty->hoary upgrade. I've found a partial workaround that I post here for information!

I looked in **.xsession-errors** and found a number of entries along the lines of:

[INDENT]Unable to open desktop file moe-0072d8654d.desktop for panel launcher[/INDENT]

Now, although I did have some .desktop files in my .gnome2 directories, they were all things I'd added since installing Ubuntu: the ones mentioned in .xsession-errors were indeed missing. So I created a file called **unable.txt** containing:

[INDENT]moe-0072d8654d.desktop
curly-00b5180b1e.desktop
moe-00afc3a532.desktop[/INDENT]

etc, and then closed my Gnome session so it wouldn't touch any files while I worked. At a command prompt (CTRL-ALT-F1) I typed:

```
for i in `cat unable.txt`; do grep $i .* -rl; done
```

Bingo! There were a stack of XML files deep in **.gconf** that contained the offending references e.g:

[HTML]<entry ...>
  <stringvalue>moe-0072d8654d.desktop</stringvalue>
</entry>[/HTML]

In the end (as I say this was only a partial solution) I had to junk my entire .gconf. I tried editing out the references, but that left my .gconf files unstable: I got the same error popup, but different reports in .xsession-errors complaining about dropped references. There's clearly some complexity and cross-references in the .gconf files that I don't understand. If anyone can suggest an elegant solution then please do.

But, anyway: **getting rid of .gconf removes this error under Dapper Drake**.

---

