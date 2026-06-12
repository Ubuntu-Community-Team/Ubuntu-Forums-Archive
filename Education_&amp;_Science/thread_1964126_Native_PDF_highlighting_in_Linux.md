---
title: "Native PDF highlighting in Linux"
date: 2012-04-23
forum: Education &amp; Science
---

### Post by demetriodn on 2012-04-23
Dear all

I have been using Ubuntu for a while now (4 years), but I am still a begginner-google-dependant user.
I dont know much about Linux, or programming, but something intrigues me.

How come after all these years developing PDF readers for linux there is still no native PDF highlighting??? Is it so difficult to achieve? 

Im getting tired of using windows softwares under Wine.

Okular and Xournal are not options, you cannot save the annotations to the PDF files and if you do, other PDF readers do not recognize it.

Could somone explain me why there is still no native PDF reader with Highlight in Linux???

---

### Post by zerubbabel on 2012-04-23
I haven't found any native Linux tools for annotating pdfs, but PDF XChange Pro works very well under Wine, and allows import and export of annotations in standard Adobe Acrobat fdf format. It's not free, but it packs a lot of power for $38 for the Pro version.

---

### Post by entropy1 on 2012-04-23
With xournal, you can export to pdf, and then read the new pdf file with any pdf read such as acrobat reader or evince.

Example:

You have file.pdf

Open file.pdf with xournal, and then save it as fileComments.xoj.  Now add comments and save; do not close xournal yet.  Select File > Export to PDF
in order to create fileComments.pdf.  Now you have a pdf file with comments.  As an alternative to using Export to PDF, you could Print to PDF.

---

### Post by rewyllys on 2012-04-23
> **demetriodn said:**
> Dear all

I have been using Ubuntu for a while now (4 years), but I am still a begginner-google-dependant user.
I dont know much about Linux, or programming, but something intrigues me.

How come after all these years developing PDF readers for linux there is still no native PDF highlighting??? Is it so difficult to achieve? 

Im getting tired of using windows softwares under Wine.

Okular and Xournal are not options, you cannot save the annotations to the PDF files and if you do, other PDF readers do not recognize it.

Could somone explain me why there is still no native PDF reader with Highlight in Linux???
I have been quite happy with PDF Studio Pro, which does just about everything that Adobe Acrobat does.  And it costs much less than Adobe Acrobat.

PDF Studio Pro is available in a native Linux version from
[http://www.qoppa.com/pdfstudio/index.html]("http://www.qoppa.com/pdfstudio/index.html")

---

### Post by demetriodn on 2012-04-24
zerubbabel: that is the software I have been using ever since I started with Ubuntu, but it lacks integration with other linux apps.

entropy: did you notice the number of steps one should follow to accomplish something that SHOULD be very simple? And it is very simple in a lot of Windows software. Remember also that you cant view page thumbnails with Xournal.

rewyllys: thanks for the advice, I think I'll give it a try

So again, why is it so difficult to do it in Linux?

---

### Post by haqking on 2012-04-24
read this thread

[http://ubuntuforums.org/showthread.php?t=1954815](http://ubuntuforums.org/showthread.php?t=1954815)

---

### Post by PGScooter on 2012-04-24
For highlighting and annotating, Mendeley is great. It is free but proprietary. It is not a pdf editor, but highlighting and annotating work great. I think they are adding more colors to highlight in also.

---

### Post by demetriodn on 2012-04-24
Yes, I'm using Mendeley as a Zotero complement, because of the ease of acessing the PDFs. The PDF interface is excellent, the only problem is that Mendeley does not save the annotations to the PDF, so you can't share your articles with your colleagues (only if they use Mendeley too) or open them in another software. I would really be a good alternative if it could save to the PDF, better yet if they release a standalone version of the reader.

---

### Post by PGScooter on 2012-04-24
> **demetriodn said:**
> Yes, I'm using Mendeley as a Zotero complement, because of the ease of acessing the PDFs. The PDF interface is excellent, the only problem is that Mendeley does not save the annotations to the PDF, so you can't share your articles with your colleagues (only if they use Mendeley too) or open them in another software. I would really be a good alternative if it could save to the PDF, better yet if they release a standalone version of the reader.

Are you sure? Are you using the most recent version (from PPA) ? I haven't used Mendeley recently but I thought that they implemented this feature. I would be interested in knowing. Are you sure that the pdf reader that you're using doesn't have problems *reading* the annotations ?

---

### Post by haqking on 2012-04-24
> **Helen09 said:**
> [IMG]<snip>[/IMG]Im getting tired of using windows softwares under Wine.

Then dont use it.

There are plenty of alternatives and or using Virtual machines

---

### Post by demetriodn on 2012-04-25
PGScooter: Unfortunately Mendeley does not save the annotations to the PDF. This is a longtime request of the Mendeley community:
[http://feedback.mendeley.com/forums/4941-mendeley-feedback/suggestions/985703-pdf-annotations-should-be-compatible-with-other-pd]("http://feedback.mendeley.com/forums/4941-mendeley-feedback/suggestions/985703-pdf-annotations-should-be-compatible-with-other-pd")

---

### Post by PGScooter on 2012-04-25
> **demetriodn said:**
> PGScooter: Unfortunately Mendeley does not save the annotations to the PDF. This is a longtime request of the Mendeley community:
[http://feedback.mendeley.com/forums/4941-mendeley-feedback/suggestions/985703-pdf-annotations-should-be-compatible-with-other-pd]("http://feedback.mendeley.com/forums/4941-mendeley-feedback/suggestions/985703-pdf-annotations-should-be-compatible-with-other-pd")

good to know! Hopefully they implement that.

---

### Post by vandroiy.cl on 2013-01-14
Hi, i was reading this thread and i realize that no one mentioned Foxit, as another non native solution. It allows you to annotate, highlight, and save what you've done in the same file. Mostly any other reader will display the saved annotations without trouble.

I use foxit reader 4.2 through Wine, and it works really good, it opens like a portable app, and I had no problems adding it to the menu or making it the default reader. 

I recommend to use 4.2 because newer version added unnecessary features. I think it's really good and doesn't use a lot of resources either.

---

### Post by Abhinav Kumar on 2013-01-14
> **rewyllys said:**
> I have been quite happy with PDF Studio Pro, which does just about everything that Adobe Acrobat does.  And it costs much less than Adobe Acrobat.

PDF Studio Pro is available in a native Linux version from
[http://www.qoppa.com/pdfstudio/index.html](http://www.qoppa.com/pdfstudio/index.html)
+1 for PDF Studio from Qoppa Software. A really nice PDF editor

---

### Post by demetriodn on 2013-01-14
> **Abhinav Kumar said:**
> +1 for PDF Studio from Qoppa Software. A really nice PDF editor

Yeah, allright. I can understand why you like this software:

> Do you love PDF Studio and want to spread the word? For a limited time, help us promote our software and send us 3 links from PDF related websites or forums where you've recommended or reviewed PDF Studio. To thank you, we will send you a free license key for PDF Studio Pro.

It is good, indeed. It works very well under ubuntu. I would pay 20 dolars for this, but $89 for the standard????

---

### Post by Abhinav Kumar on 2013-01-15
> **demetriodn said:**
> Yeah, allright. I can understand why you like this software:
Hi,
I had used it and it was working fine. I had not recommended it to get any key.

Regards,
Abhinav

---

### Post by Warthaug on 2013-01-15
Mendeley now allows export of PDFs with highlights and annotations.  The option is found under the file menu.

---

### Post by rewyllys on 2013-01-17
Since Demetriodn has chosen to question Abhinav Kumar's honesty and mine, I should like to set the record straight concerning my recommendation of PDF Studio Pro.  Here are the facts:
 
[LIST=1]
[*]I **purchased PDF Studio 7     Professional** (scil., the “**Pro**” version) **over a     year ago**.  I did **not** purchase, and have **not** used,     the **“standard”** version
[*]I was **unaware** of Qoppa's     **offer of an upgrade from the “standard” version to the “Pro”     version before** I saw Demetriodn's post #15.
[/LIST]

---

### Post by sankeytm on 2013-01-30
Okay, now you can all uninstall wine and shut down your virtual machines... Okular supports saving annotations *and* they show in other PDF viewers.

---

### Post by pagalacoca on 2013-02-13
> **sankeytm said:**
> Okay, now you can all uninstall wine and shut down your virtual machines... Okular supports saving annotations *and* they show in other PDF viewers.

I've made annotations with Okular, but they don't show in other PDF viewers, only in okular. The other viewers I'm using are evince and Mendeley.

---

### Post by TheFu on 2013-02-13
> **zerubbabel said:**
> I haven't found any native Linux tools for annotating pdfs, but PDF XChange Pro works very well under Wine, and allows import and export of annotations in standard Adobe Acrobat fdf format. It's not free, but it packs a lot of power for $38 for the Pro version.

No need for the Pro version of PDF-Xchange to annotate files. I've been using the free version  (v2 build 54)  for a few years just fine to add notes to corporate bank statements so our accountants know what things are.  I haven't bothered to load this in WINE either, but I'll trust what others say about it working well.

We would all prefer a native solution that actually writes the annotations in the PDF standard way, but every time I looked, it was not to be.

---

### Post by monkeybrain2012 on 2013-02-14
> **pagalacoca said:**
> I've made annotations with Okular, but they don't show in other PDF viewers, only in okular. The other viewers I'm using are evince and Mendeley.
 If you print it instead of save it the annotations will show.

---

### Post by sankeytm on 2013-02-18
> **pagalacoca said:**
> I've made annotations with Okular, but they don't show in other PDF viewers, only in okular. The other viewers I'm using are evince and Mendeley.

I'm using Okular 0.15.5 in KDE 4.9.5 and the highlights are visible in Evince and Adobe Reader (only tested these two).

> **monkeybrain2012 said:**
> If you print it instead of save it the annotations will show.

You only need to press save, at least with Okular 0.15.5.

---

