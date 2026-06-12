---
title: "SCITE crashing when started from menu"
date: 2006-07-08
forum: Desktop Environments
---

### Post by fuxoft on 2006-07-08
I have the lates SCITE package installed and when I run the program from Applications/Programming menu, it starts but crashes immediately when I click on the "File" item in the toolbar (the menu does not even appear). I tried about 20 times and it crashes ALWAYS. I also tried running it from the commandline and then it only crashes sometimes (with "Segmentation fault" message). Clicking on other item than "File" also crashes it but not always. The only combination that crashes it always is opening SCITE from the menu and clicking "File" (however, it SOMETIMES crashes under other conditions making it very painful experience). I tried running it with strace and got this:

```
uname({sys="Linux", node="frantisek", ...}) = 0
gettimeofday({1152373069, 141824}, NULL) = 0
poll([{fd=3, events=POLLIN}, {fd=4, events=POLLIN}], 2, 0) = 0
gettimeofday({1152373069, 142101}, NULL) = 0
poll([{fd=3, events=POLLIN}, {fd=4, events=POLLIN}], 2, 0) = 0
gettimeofday({1152373069, 142339}, NULL) = 0
poll([{fd=3, events=POLLIN}, {fd=4, events=POLLIN}], 2, 0) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

```

Purging and reinstalling scite package had no effect.

---

