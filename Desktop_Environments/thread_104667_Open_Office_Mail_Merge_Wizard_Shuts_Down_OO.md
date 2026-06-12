---
title: "Open Office Mail Merge Wizard Shuts Down OO"
date: 2005-12-16
forum: Desktop Environments
---

### Post by Roman27 on 2005-12-16
Has anyone tried creating a mail merge in OO?  I open writer, go to *Tools* and then *Mail Merge Wizard*.  The wizard starts.  I choose, *Use current document* and then click *Next*.  I choose *Letter* and then click *Next*.  ***POOF***  Open Office shuts down.  No error message of any kind.

Anyone have a clue what the issue is?

---

### Post by wrtrdood on 2005-12-16
I'm not where I can check that but one guess would be that you have to set up an address list source first.  Seems I remember a similar symptom to what you describe but that was ages ago (OOo 1.1, I think).  I can't believe it's still a problem.

---

### Post by David Valentine on 2006-03-31
I had this happen to me on one of my boxes, but not the other, at exactly the point you referred to.  I did, however, get a post-crash error message that referenced libkmod (I think).  The major difference between my two boxes is that the one giving me the problem is the one on which I also added kde.  I'm planning to get rid of kde on that box, and then see if it works.

---

### Post by nonemlinus on 2006-06-15
I had a similar problem with Open Office Writer (oo 2.0.2 under dapper).
  
Everything had been working fine until I tried starting one of the 'wizard's.
(File->Wizards->Letter...)  Attempting to start the wizard crashed the application.

However, I did two things and one seemed to help.
I changed the following options (Tools->Options; under OpenOffice.org->):
        * under ->UserData, I added my address information.
        * under ->Java, I updated the path to Sun's 1.5 jre which I had
                              installed after the initial fresh dapper installation.

I'm sure the java setting helped since I'm guessing the wizards 
are jar files (I haven't really looked into this though...)
...or maybe the address information.  Not sure which one fixed it
but, the wizard seems to start up ok now and there's no crash.

Hope that helps, 
Sunil

---

