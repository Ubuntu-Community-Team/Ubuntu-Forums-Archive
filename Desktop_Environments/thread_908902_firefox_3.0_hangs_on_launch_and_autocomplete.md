---
title: "firefox 3.0 hangs on launch and autocomplete"
date: 2008-09-02
forum: Desktop Environments
---

### Post by outerboundofeternity on 2008-09-02
recently my firefox intsall begain taking 3 minutes to launch (use to be 5 seconds). when it does launch, autocomplete in any bar(address, search window) locks firefox for two minutes. Pages take about a minute to load. Am runing xubuntu 8.04 on a p4 3.4ghz with 2gb of ram. It used to run lickedy split fast, then overnight slow. ran update, purged firefox and reinstalled with no luck. looking for ideas/help. (firefox 2 works fine.)

---

### Post by mali2297 on 2008-09-03
Open firefox from the terminal by typing *firefox-3.0*. Do you see any warnings or error messages printed in the terminal?

---

### Post by outerboundofeternity on 2008-09-06
nope, says absolutely nothing on the command line.

---

### Post by mali2297 on 2008-09-06
Have you cleared cache, cookies etc?

You can also try removing the **.mozilla** folder in your home directory. Or rather, rename it .mozilla.backup or something. The folder contains your bookmarks, extensions etc.

---

