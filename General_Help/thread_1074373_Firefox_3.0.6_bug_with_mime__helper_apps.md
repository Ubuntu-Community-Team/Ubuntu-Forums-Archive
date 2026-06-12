---
title: "Firefox 3.0.6 bug with mime / helper apps"
date: 2009-02-19
forum: General Help
---

### Post by mtrainer on 2009-02-19
Hi,

I am using the latest Firefox 3.0.6 update on Kubuntu 8.04 64-bit.  When I download a MS .doc file most often it recognizes the file as a Microsoft Word Document and offers to open the file with OpenOffice.  Occasionally though it fails to recognize the file properly (as a .DOC file) and offers to Save the file or Open with (Browse) a program.  It appears to be an intermittent problem - if you click on the link below enough times you will hopefully see what I mean:

[http://www.xmlw.ie/aboutxml/wordsample2.doc](http://www.xmlw.ie/aboutxml/wordsample2.doc)

Can anyone else reproduce this?  Interestingly, if I save the file locally and browse with Firefox, I get the same problem sometimes.

Thanks

Murray

---

### Post by mtrainer on 2009-02-19
> **mtrainer said:**
> Hi,

I am using the latest Firefox 3.0.6 update on Kubuntu 8.04 64-bit.  When I download a MS .doc file most often it recognizes the file as a Microsoft Word Document and offers to open the file with OpenOffice.  Occasionally though it fails to recognize the file properly (as a .DOC file) and offers to Save the file or Open with (Browse) a program.  It appears to be an intermittent problem - if you click on the link below enough times you will hopefully see what I mean:

[http://www.xmlw.ie/aboutxml/wordsample2.doc](http://www.xmlw.ie/aboutxml/wordsample2.doc)

Can anyone else reproduce this?  Interestingly, if I save the file locally and browse with Firefox, I get the same problem sometimes.

Thanks

Murray

This is a pretty serious bug, surely someone else can reproduce it ...

---

### Post by Yashiro on 2009-02-19
It's your machine. It works 100% fine here.
Ubuntu 8.04 (gnome) / FF 3.0.6

---

### Post by mtrainer on 2009-02-19
> **Yashiro said:**
> It's your machine. It works 100% fine here.
Ubuntu 8.04 (gnome) / FF 3.0.6

Thanks for your reply.  Looks like it's OK for Gnome users.  I'm getting the issue on 3 different machines with FF 3.05.  I am using KDE 3.5.5 and don't have Gnome installed.  I don't have gconf installed either on any of them and should not need to to have Firefox work properly in KDE.  It should work without any Gnome components installed.  Obviously Firefox isn't handling KDE mime associations properly every time.

Murray

---

