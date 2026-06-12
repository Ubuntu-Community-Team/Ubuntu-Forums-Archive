---
title: "Marvinbeans"
date: 2011-09-13
forum: Education &amp; Science
---

### Post by ah535 on 2011-09-13
Hey guys I am super new to Linux and I am trying to get a good chemdraw program, but I am running into some problems.  I first went to. [http://www.chemaxon.com/marvin/download.html](http://www.chemaxon.com/marvin/download.html).  From there I clicked on End Users (I have no clue what that means).  I clicked Linux installer with Java.  

When I click **Places>Download **then i see a file that says** marvinbeans-5.6.0.0-linux.sh **when I right click and run with Sun Java is says** marvinbeans-5.6.0.0-linux.sh' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.** What should I do?

---

### Post by ah535 on 2011-09-21
::bump::

---

### Post by rewyllys on 2011-09-22
> **ah535 said:**
> Hey guys I am super new to Linux and I am trying to get a good chemdraw program, but I am running into some problems.  I first went to. [http://www.chemaxon.com/marvin/download.html](http://www.chemaxon.com/marvin/download.html).  From there I clicked on End Users (I have no clue what that means).  I clicked Linux installer with Java.  

When I click **Places>Download **then i see a file that says** marvinbeans-5.6.0.0-linux.sh **when I right click and run with Sun Java is says** marvinbeans-5.6.0.0-linux.sh' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.** What should I do?
Click on Places-->Download; right-click on marvinbeans-5.6.0.0-linux.sh; and choose Properties. In the window that opens, click on the Permissions tab; then check the box corresponding to "Allow executing file as program"; and then click on Close.

Then open Terminal; enter "cd ~/Download" (without the quotes); then enter "sudo sh marvinbeans-5.6.0.0-linux.sh" (again without the quotes).  Provide your password, and the marvinbeans script will run.  Good luck!

---

### Post by ah535 on 2011-09-22
Thank you so much!!!

---

### Post by ah535 on 2011-09-23
Marvinsketch is awesome!!! Thank you again for the help.  This is just preference ,but I was also wondering if there was a way I could open it to **Applications->Science**.  Currently I go to Places->Downloads then I double click on Marvinsketch then I click on run.

---

