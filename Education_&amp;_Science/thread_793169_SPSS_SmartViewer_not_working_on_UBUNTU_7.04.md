---
title: "SPSS SmartViewer not working on UBUNTU 7.04"
date: 2008-05-13
forum: Education &amp; Science
---

### Post by vanale on 2008-05-13
I have managed to install SPSS 16 for Linux on my UBUNTU 7.04 according to the instructions I found here [http://ubuntuforums.org/showthread.php?t=724613](http://ubuntuforums.org/showthread.php?t=724613).

I also installed the SmartViewer app that comes with SPSS 16 to open .spo files. 

However, SmartViewer wont start. I think the launcher is file VIEWER located in SmartViewer/bin/. 

I tried to apply the same walkthrough as for SPSS launcher (see thread above); disabled compiz added the line export AWT_TOOLKIT="MToolkit" to file SmartViewer/bin/viewer. Nothing worked!

Do you have any suggestions? Has anyone made SmartViewer work on UBUNTU?

Thanks!

---

### Post by misiu369 on 2008-06-17
There are a couple of problems...

1. AFAIK, the .spo files can be opened only with v.14 or v.15.

2. There's no earlier version for Linux then v.16.

3. The LegacyViewer added to SPSS v.16 for Windows is basically a stripped version of standard SmartViewer v.15 (as mentioned above, it's Windows-only).

4. I've tried running the LegacyViewer under Windows - opened .spo correctly, but couldn't export to other formats (i.e. pdf or xls). I was also unable to copy the report (or single items) and paste it to another application (e.g. Excel).

Finally, I've found somebody with SPSS v.15 who opened the report and exported it to pdf for me. So either try v.14 or v.15 under Windows, or running it on Linux with wine (haven't tried that).

Please, post your results if you try the wine approach.

---

