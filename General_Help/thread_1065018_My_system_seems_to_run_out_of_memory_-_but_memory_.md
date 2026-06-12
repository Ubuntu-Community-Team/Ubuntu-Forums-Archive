---
title: "My system seems to run out of memory - but memory is available"
date: 2009-02-09
forum: General Help
---

### Post by MountainX on 2009-02-09
When I try to open multiple PDF documents in Evince Document Viewer (the default app), after several documents are open, Evince fails to load the next one. This always happens. 

Here are the steps I used to produce the "bug" just now:
1. check system monitor memory. It shows 1.2 GiB used of 3.0 GiB (and no swap memory used out of 3.4 GiB).
2. Open 5 PDF documents. No problems. (But Evince it gets slower at opening each new document I think).
3. Open the 6th PDF. It fails to load. No error is show, but Evince just shows me a blank window.
4. check system monitor again. It shows 1.4 GiB used of 3.0 GiB (and still no swap memory used out of 3.4 GiB).
5. if I close a previously opened PDF document, I can open the 6th one that would not open before. So it is not a problem with a specific PDF document. It appears to be a problem with how many large documents I have open. The PDF files in this test were more than 1 MB each (and largest was 11 MB).

I repeated the test with smaller PDF documents (all under 200k) and I was able to open 8 without problems and I probably could have opened more.

Any ideas?

BUG REPORT FILED: [https://bugs.launchpad.net/ubuntu/+source/evince/+bug/327327](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/327327)

---

### Post by cb951303 on 2009-02-09
I always found evince very buggy. For me it crashes too often and sometimes it refuses to load PDFs just showing white pages.

---

### Post by binbash on 2009-02-09
It sounds there is a memory leak at the software, fill a bug report

---

### Post by MountainX on 2009-02-09
What is the best PDF viewer?

I downloaded PDF Editor but I do not like the interface and I can't even figure out how to do simple stuff with it. I want something lightweight and simple like Evince, but without the bugs. Any suggestions? Thanks.

---

### Post by cb951303 on 2009-02-10
the best pdf viewer in my opinion is xpdf but it looks ugly because of the motif GUI.

okular (KDE) is quite good too

---

### Post by MountainX on 2009-02-10
> **cb951303 said:**
> the best pdf viewer in my opinion is xpdf but it looks ugly because of the motif GUI.

okular (KDE) is quite good too

I can deal with the GUI of xpdf. But what about Adobe Acrobat Reader for Linux?

---

### Post by jrusso2 on 2009-02-10
> **cb951303 said:**
> the best pdf viewer in my opinion is xpdf but it looks ugly because of the motif GUI.

okular (KDE) is quite good too

xpdf viewer is very basic all it does it view the most basic pdf.  If you want to do more then try adobe reader or foxit reader.

---

### Post by MountainX on 2009-02-10
> **jrusso2 said:**
> xpdf viewer is very basic all it does it view the most basic pdf.  If you want to do more then try adobe reader or foxit reader.

Wow, Foxit looks very cool!
[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)
Thanks

---

### Post by sharon.gmc on 2009-02-10
I think the best is PDF editor

---

