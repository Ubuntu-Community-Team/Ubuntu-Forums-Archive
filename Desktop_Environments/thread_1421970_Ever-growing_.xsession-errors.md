---
title: "Ever-growing .xsession-errors"
date: 2010-03-04
forum: Desktop Environments
---

### Post by truth is life on 2010-03-04
Due to some recent issues, I have been looking at my .xsession-errors file to see what might be prompting it to grow to improbable sizes. One particularly prominent issue is the huge number of lines marked "Debug" which contain no real information (they merely complain about the poor state of the internet connection here, or that I changed my wallpaper, or that I closed my laptop's lid). Is there any way to tell xfce to have a higher threshold before it writes errors to the log?

---

### Post by diesch on 2010-03-05
No. The messages aren't spit by XFCE but by the individual programs - everything a programs writes to the terminal when you start from the command line is written to ~/.xession-errors if you start the program from the GUI.

Please [file a bug report](https://help.ubuntu.com/community/ReportingBugs) for programs spitting out excessive messages.

---

