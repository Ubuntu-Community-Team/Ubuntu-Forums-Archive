---
title: "Biblioscape under Wine - &quot;Cannot open AVI&quot;"
date: 2006-08-15
forum: Desktop Environments
---

### Post by cwmccabe on 2006-08-15
I installed the 30 day trial version of Biblioscape 6.6 on Kubuntu (Dapper 6.06) and I'm having a problem getting it to run.  It starts up cleanly, but when I try to save changes to any records it pops up an alert saying, "Cannot open AVI". The program then becomes unresponsive, not allowing other records to be openned.  The changes to the record are saved, but I have to restart Biblioscape to get the program to work again.

Has anyone else experienced this problem when using Biblioscape under Wine?  More importantly, can anyone suggest a solution so that I can get it running?

My office is currently heavily invested in using Biblioscape, so this is really important for us when trying to use Linux.  So, any help anyone can give would be very *greatly* appreciated!!

Thanks!

=================================================================
**EDIT**:

I fixed the problem and the solution was very simple.  All I had to do was use a newer version of Wine than is in the standard Ubunutu repositories. 

I installed the newer version by adding the following line to my repositories list:
*deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main*

Ubuntu-specific instructions and more info here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

