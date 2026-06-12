---
title: "Printing PDFs"
date: 2009-06-02
forum: General Help
---

### Post by Kismet on 2009-06-02
I'm trying to print a couple PDFs and failing horribly.

If I type 'lpr xxxx.pdf' My memory usage sky rockets.

Running 'top' I can see that a process named 'pdftopdf' is eating up ALL my memory. I watched it grow to over 2GB trying to print a 1mb pdf. Is this something anyone has ran into before, or should I file a bug report.

I swear earlier this year I was able to print pdf's successfully, so this may be a bug introduced in a cups update.

Any suggestions are appreciated.

---

### Post by khelben1979 on 2009-06-02
Why not print the pdf file within the application instead?

---

### Post by Kismet on 2009-10-08
Because scripts and cron jobs are better suited to the CLI. :)

Just thought I'd update this, it was a bug.

The command 'pdftops' suffered an infinite loop on some PDF files. This has been remedied in newer releases.

---

