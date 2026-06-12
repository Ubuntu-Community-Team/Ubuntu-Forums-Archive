---
title: "Urban Terror install error"
date: 2007-11-17
forum: Gaming &amp; Leisure
---

### Post by stomponthis on 2007-11-17
Hi all
I am having a little problem installing Urban Terror.  I am using the script that is available on their website from here : [http://www.urbanterror.net/page.php?6]("http://www.urbanterror.net/page.php?6")
The following is the output from the terminal.
```
Verifying UrbanTerror40_full.zip integrity ...OK
Extracting Linux ELF binaries ...
Archive:  ioUrbanTerror_Installer_1.0.zip
caution: filename not matched:  nautilus-debug-log.txt
ERROR: Archive extraction failure.
```
Any ideas?

---

### Post by Trumpen on 2007-11-26
The script you were using contains a *.txt which is expanded by the shell during the execution. In your case it was expanded to "nautilus-debug-log.txt". 

To resolve the problem just protect *.txt with double quotes at line 230 of the script:

```
${unzip_bin} -u -d ${destpath} ${iob_zip} "*.txt" || err_extract
```

Hope this helps!

Trumpen.

---

