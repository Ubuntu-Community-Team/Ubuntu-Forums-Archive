---
title: "Discussion - https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu"
date: 2012-07-16
forum: Documentation and Community Wiki Discussions
---

### Post by wildmanne39 on 2012-07-16
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu](https://help.ubuntu.com/community/BuildnewestversionofBluefishforUbuntu)

Support threads should be posted in normal forums.

Thank you

---

### Post by Toz on 2012-07-16
A new version 2.2.3 is now available. You may wish to re-test these steps and update the document.

The code in the "Download source code, open tarball, compile and install with one command" doesn't work. ( &amp;&amp; ) I think something may have gotten lost in the translation.

However, for the sake of clarity and ease of understanding, I would recommend splitting up the "Download source code, open tarball, compile and install with one command" into separate steps.
- Download source code
- Extract tarball
- Compile
- Install

Might also be helpful if you mentioned an uninstall script if its supported (make uninstall).

---

### Post by wildmanne39 on 2012-07-16
Hi Toz, I fixed the first set of commands to where they will work with precise it was really easy thanks to the great work of andrew.46 and I removed the bad parts that were put into the code during translation. 

I would have seen them but I am on a small laptop at the moment and my eye sight is not the good, I usually use a 24 inch monitor with large text.
Thanks much appreciated.

---

### Post by andrew.46 on 2012-07-25
I have reformatted a little and updated for 2.2.3. Thanks for the conversion to wiki :).

---

### Post by wildmanne39 on 2012-07-25
Hi andrew.46, thank you for updating the wiki with the latest version, it looks great!!!

---

### Post by andrew.46 on 2012-07-25
Well, it will be interesting. I have had my doubts about the move to the Ubuntu Wiki so I am watching with some interest developments for this Bluefish guide. Thanks again for the conversion :).

---

### Post by ads52 on 2012-08-10
I must say that as well as the usual bug fixes and improvements Bluefish 2.2.3 *looks *much nicer than the previous version :).

---

### Post by ads52 on 2012-08-13
In the world's smallest improvement to the wiki guide I have altered the checkinstall syntax to clean up the installation of the docs.

---

### Post by wildmanne39 on 2012-08-13
Nice work! thanks for keeping the wiki updated!

---

### Post by ads52 on 2012-08-13
> **wildmanne39 said:**
> Nice work! thanks for keeping the wiki updated!

andrew.46 is gone now, but I intend to continue at least *some* of his work :).

---

### Post by xphrog on 2012-09-04
I should not have followed these instructions!!  I misunderstood completely -- thinking that when I read 

> This following code block(s) downloads, compiles **and install**(s) Bluefish  2.2.3. Checkinstall builds a neat package that integrates into the  Ubuntu package management system:that all I would need to do afterwards was type "bluefish" and I would be off to the races without the configuration file error I kept getting from the version I had installed from the Ubuntu repository.

(Though I could not read  all of the pages and pages of text generated in terminal, I did not see any major error notifications; the install claimed to have been successful, despite passing a few deprecated packages along the way.)

I suspect I am going to have to reinstall Ubuntu to get rid of all these packages I downloaded and remove whatever it is that is tricking Ubuntu Software Center into thinking I have a version of "bluefish" installed?  But as a thorough newbie, I thought I would at least ask if I am missing something blatantly obvious before trying [COLOR=Purple]sudo apt-get remove bluefish[/COLOR] or a reinstall.  I was so looking forward to working tonight; this will teach me to try to go outside the repositories to get around a missing config file that didn't prevent my little blue fish from working swimmingly.  

I have looked at the INSTALL and the README pages (I did try typing "bluefish-unstable" to no avail), but must admit, I'm a clueless newbie, having never compiled a program before...   

Is there an undo button somewhere?  :lolflag:

---

