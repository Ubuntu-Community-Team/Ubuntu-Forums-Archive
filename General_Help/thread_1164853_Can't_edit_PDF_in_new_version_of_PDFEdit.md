---
title: "Can't edit PDF in new version of PDFEdit"
date: 2009-05-20
forum: General Help
---

### Post by ToshibaLaptoplinux on 2009-05-20
I have been a relatively long time user of PDF Edit primarily on Feisty and Hardy. It has always served me well and worked relatively flawlessly.

Since updating my machine to Jaunty (Clean install) I can not edit any linearized PDF's with PDFEdit (v4.1). When I select the Delinearize option I can't edit that document either. All of the editing options are grayed out.

This behavior is also exhibited if I open documents that I had previously successfully edited in the past. Any ideas? I regularly edit a lot of PDF's so this is kind of critical for me.

Since it was a bit of an emergency I downgraded to the version I was using on Hardy (3.1?) and have no problems editing...BUT...I would like to use the newer version that came through th eJaunty repo's because it is supposedly "better supported".

Thanks.

Thanks.

---

### Post by labinnsw on 2009-05-20
If you are willing to try another software and don't mind free versions of commercial software, give [PDF-XChange PDF Viewer]("http://www.docu-track.com/home/prod_user/PDF-XChange_Tools/pdfx_viewer") a go. It is an extremely versatile piece of software. It is a windows software that works smoothly with wine.

It is a good alternative until help arrives to fix PDFEdit. You might never go back.

---

### Post by luigi_mb on 2009-05-20
> **ToshibaLaptoplinux said:**
> I have been a relatively long time user of PDF Edit primarily on Feisty and Hardy. It has always served me well and worked relatively flawlessly.

Since updating my machine to Jaunty (Clean install) I can not edit any linearized PDF's with PDFEdit (v4.1). When I select the Delinearize option I can't edit that document either. All of the editing options are grayed out.

This behavior is also exhibited if I open documents that I had previously successfully edited in the past. Any ideas? I regularly edit a lot of PDF's so this is kind of critical for me.

Since it was a bit of an emergency I downgraded to the version I was using on Hardy (3.1?) and have no problems editing...BUT...I would like to use the newer version that came through th eJaunty repo's because it is supposedly "better supported".

Thanks.

Thanks.

If you go to 

[http://sourceforge.net/projects/pdfedit](http://sourceforge.net/projects/pdfedit)

you can download the source for v4.2. It compiled easily here (Ubuntu 9.04), after getting some needed libs (see output of ./configure). 

It works very well.

/luigi

---

