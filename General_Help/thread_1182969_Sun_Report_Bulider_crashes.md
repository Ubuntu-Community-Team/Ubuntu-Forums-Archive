---
title: "Sun Report Bulider crashes"
date: 2009-06-09
forum: General Help
---

### Post by peterroots on 2009-06-09
Using kubuntu8.04 and sun report builder 1.0.5 installed via the package manager in openoffice I was able to open and edit reports.

Using Kubuntu9.04 I could not open or edit reports.  If I removed report builder I could use the ooo report wizard but not open or edit the reports created in sun report builder (no surprise there).
I then found if I reinstalled report builder and then installed openoffice.org-report-builder-bin from the ubuntu repositories I could now open and edit reports again. Unfortunately closing the report or edit window now caused ooo to crash.  The document recovery dialogue does not contain a 'next' button to generate a crash report but does have a recover button to get the doc back again.
I then tried removing the sun report builder plugin, installed via the ooo package manager, and installed it via the Ubnuntu repositories but this also gave the same behaviour.
Any ideas?

I have just tried installing the openoffice.org-gcj package and then deselected the java runtime to see if this had any effect - I could not open a report at all with this.  I have also tried java-6-sun-1.6.0.13 java-6-openjdk and free software foundation 1.5.0 runtimes, all of which allow me to open/edit the reports but all crash on close.

---

### Post by peterroots on 2010-02-13
Just for the record, quite some time ago I upgrade to kubuntu 9.10 and installed ooo and the report builder from repository rather than the plugin - it all worked fine.

---

