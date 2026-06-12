---
title: "Limits in LyX?"
date: 2010-03-28
forum: Education &amp; Science
---

### Post by MrNatewood on 2010-03-28
Anyone knows how to make limits appear "properly" in LyX?

I mean something of the form:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151696&stc=1&d=1269777584[/IMG]

Where x->a is beneath the "lim"

---

### Post by gmjs on 2010-03-28
Create the limit with the subscript option, then highlight the range and choose **Edit > Math > Change Limits Type > Display**.

Hope this helps,

Graham

---

### Post by MrNatewood on 2010-03-28
That works :)
Thanks.

BTW, any idea on how to export to an image(png/jpg/gif)?

---

### Post by gmjs on 2010-03-30
Not something I've done.  This looks like it will do exactly that, but I failed to compile one of the required components (Netpbm 9.24).  You're Linux skills are probably better than mine though!

[http://www.fourmilab.ch/webtools/textogif/textogif.html]("http://www.fourmilab.ch/webtools/textogif/textogif.html")

Alternatively, you could export a PDF document with all the equations you want on it and then extract them with a PDF viewer (not evince I don't think, but KPDF or Adobe PDF have a 'copy graphic to clipboard') option.

---

