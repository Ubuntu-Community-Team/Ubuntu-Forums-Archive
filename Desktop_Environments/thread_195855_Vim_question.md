---
title: "Vim question"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Hanj on 2006-06-13
I'm trying to open a html file with Vim, but there's some problem with the encoding, causing a problem with newlines. The entire file is shown as one single line and where there should be a line break I see a "^M" instead. Gedit opens the file correctly though. Any Vim users out there who know how I can change the way Vim opens the file? Or is there some other way to fix it?

---

### Post by kabus on 2006-06-13
Maybe this will help:
[http://www.vim.org/tips/tip.php?tip_id=26](http://www.vim.org/tips/tip.php?tip_id=26)

---

### Post by IYY on 2006-06-13
Was this file made in Windows and then transferred to Linux in binary mode?

---

### Post by Hanj on 2006-06-13
Thanks Kabus, that's what I needed! :D
For some reason though, all the solutions on that page replaces the line breaks with spaces. However doing :%s/^M/\r/g solved the problem. The trick was to write ^M with ctrl-V ctrl-M.

---

