---
title: "Opening a file in Terminal with a specific program"
date: 2008-06-04
forum: Desktop Environments
---

### Post by nomizzz on 2008-06-04
How does one go about opening a specific document "with" a specific program in terminal?  

I'm trying to create a new launcher for my top panel in GNOME that opens my GNU Cash Finance archive with the GNU cash program.  I've read about the "gnome-open" command, but this doesn't quite meet my needs as Ubuntu just views the file as a standard zip archive and tries to gzip it.

Any ideas?

---

### Post by Rigrig on 2008-06-04
Have you tried ```
gnu-cash-program *path_to_cash_finance_archive*
```

---

### Post by nomizzz on 2008-06-04
> **Rigrig said:**
> Have you tried ```
gnu-cash-program *path_to_cash_finance_archive*
```

Actually, it was almost easier than that...  It turned out to be just: ```
gnucash "path to finance archive"
```

DUH!](*,)

Thanks for the help.

---

