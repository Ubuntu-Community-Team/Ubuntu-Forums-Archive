---
title: "Simple PDF question"
date: 2006-04-08
forum: Desktop Environments
---

### Post by flebber on 2006-04-08
Is there any PDF programs I can use to "highlight" or mark sections in the document, I found I can bookmark but I cannot seem to highlight or add comment to anything. 

I have the adobe reader and xpdf and I tried kghostview, the allow me to read but I cannot highlight or comment . Any Ideas ?

---

### Post by karthik085 on 2006-04-09
Probably there is a plugin to do this.
I know some plugins are bundled in a package and exist in the respo:
acroread-plugins
But, don't know if it will solve your problem. Anyway, try installing it and see if it helps. 

[QUOTE=flebber]Is there any PDF programs I can use to "highlight" or mark sections in the document, I found I can bookmark but I cannot seem to highlight or add comment to anything. 

I have the adobe reader and xpdf and I tried kghostview, the allow me to read but I cannot highlight or comment . Any Ideas ?[/QUOTE]

---

### Post by flebber on 2006-04-09
That doesn't ad the functionality instead allows me to share docs remotely. 

Does anybody no of a program that can do highlighting to PDF files adding comments and bookmarks even if I have to change formats to something more user friendly.....

---

### Post by rfruth on 2006-04-09
How about a screen capture then convert to PDF OR spend the bucks and get the full version of adobe ;)

---

### Post by flebber on 2006-04-10
I never really wanted to use PDF , but found a few docs that would help me learn linux networking better namely olaf Network admin guide and some advanced bash docs, however I am the sort of person that needs to highlight things and mark to go back again later.

I guess I thought that highlighting would be standard, I guess I though wrong.

---

### Post by lowey23 on 2006-04-10
G'day flebber,

This is probably a really stupid question but did you give kpdf a try? I don't know if it will do what you want but it may be worth a try if you have'nt already.

Cheers

Lowey

---

### Post by flebber on 2006-04-10
Thanks Lowey yeah tried that one Xpdf, Kpdf and Gpdf are largely the same, cheers for the idea tho.

---

### Post by brodock on 2006-06-08
i was looking for something similar...
have you found anything usefull?

---

### Post by jonnymccullagh on 2006-06-12
Have you tried Kpdf - I'm pretty sure the latest version has a highlighter pen.
jonny

---

### Post by brodock on 2006-06-13
don't have...
at least they don't mention at the changelog

---

### Post by jetpeach on 2006-06-13
KPDF does not yet have this functionality, though it is on the [Wishlist for KPDF]("http://wiki.kde.org/tiki-index.php?page=KPDF").  Maybe soon, hopefully.

Also, in my quest for exactly the same thing you desire, I've posted at this thread [Adobe Acrobat in Ubuntu?]("http://ubuntuforums.org/showthread.php?t=168395") in which many others desire this type of functionality (and in that thread, I post to another thread where many others desire this!).  I also tried the following:
installing full version adobe with WINE - requires internet explorer, so installed that first.  nope, acrobat 7 still complains in Wine :(
so I tried ScanSoft's pdf editor also under Wine, and another Windows native PDF editor under wine.  One required Office to be installed (ridiculous!) the other worked but was so lame I wouldn't be able to stand it.  It also crashed, so didn't seem particularly stable under wine.

In the other thread mentioned above, people mention all sorts of round about crummy ways to edit PDFs (like using Abiword or OpenOffice or a Ghostview) but they all don't work reliably - they mess up formatting or don't save correctly etc...

So I'm still SOL on this as well and have tried pretty hard for it.  I boot into Windows when I need to read and mark up the publications I read.  Hopefully the wishlist for KPDF will happen. and soon.  Maybe we should try to convince someone that this is high priority!

---

### Post by jetpeach on 2006-07-11
Just an update on the Wine progress for Acrobat - they've been working hard over there.  I got Acrobat 7 installed, but it crashed after startup.  The new version of Wine (.9.17) makes it run as well but Scott Ritchie will hopefully in a day or two add it to the Wine repository (see [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) for install instructions)
Then [file your bugs with acrobat here]("http://appdb.winehq.org/appview.php?iVersionId=4922") if you're running Acrobat full with Wine.

Of course, I'm hopeful someday for better editing support in KPDF, but for now...

---

### Post by karthik085 on 2006-07-11
> **jetpeach said:**
> Just an update on the Wine progress for Acrobat - they've been working hard over there.  I got Acrobat 7 installed, but it crashed after startup.  The new version of Wine (.9.17) makes it run as well but Scott Ritchie will hopefully in a day or two add it to the Wine repository (see [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) for install instructions)
Then [file your bugs with acrobat here]("http://appdb.winehq.org/appview.php?iVersionId=4922") if you're running Acrobat full with Wine.

Of course, I'm hopeful someday for better editing support in KPDF, but for now...
Doesn't Adobe Reader 7.0.8 for Linux support this? You don't need wine to run it. That's even better.

---

### Post by jetpeach on 2006-07-12
No there a lots and lots and lots of features that Adobe Reader does not do.  The most important to me are highlighting and adding simple notes to PDFs.  It is unfortunate that while these seem like quite simple features, there are no native linux programs that can do it without doing massive conversion to postscript then back (->loss of formating...) etc. etc...

---

### Post by jonza on 2006-07-12
Have you tried Foxit reader. I havent tried the linux version. It has simple editing capabilities, and its incredibly fast and small. Linux version is somekind of an preview. Also the windows version might work with wine...

[http://www.foxitsoftware.com/pdf/rd_linux.php](http://www.foxitsoftware.com/pdf/rd_linux.php)

---

### Post by jetpeach on 2006-07-13
Wow, that Foxit Reader linux version demo is pretty cool - it seriously starts in less than 1/2 a second.  And it loads PDFs almost instantly.  Good to see they made a linux version.  And there's no install necessary, it's just a simple standalone app I just untarred, double clicked and it worked.

But huge drawbacks make it unusable right now - the linux version available (evaluation version) will only display the first page of a PDF and it is only a reader version, so it cannot do any highlighting or editing...

If I get a chance, I may try the full version using WINE (Windows only right now).

On another note, is anybody good at making debs from source?  I'm looking forward to  Wine 0.9.17 but it's not in the Wine repository (deb [http://wine.budgetdedicated.com/apt/](http://wine.budgetdedicated.com/apt/) dapper main) yet --- scratch that, it must've just gotten in there since yesterday. It's being upgraded now on my computer, I'll let you know how well Adobe Acrobat Professional works after it finishes.

---

### Post by kko1 on 2006-07-26
> If I get a chance, I may try the full version [Acrobat] using WINE.

Ok, so did it work?

;-)

---

### Post by jetpeach on 2006-07-26
Oh, sorry forgot to get back to this.  I can't get it working still.  It does the same thing as it did in .9.16 for me - install takes a long time, but seems to work but not confirmation (probably craps out before finishing something), can load up Acrobat fine, I can click the menus and everything, then crash/quit after about 5 seconds.  I will try to post a bug report to the wine developers with debugging data, but too busy.  Once somebody gives them the crash data, they might be able to fix very quickly (they are fast), but for now I just hope it gets fixed in the next release (0.9.18) although this seems unlikely without a bug report.

---

### Post by brodock on 2006-08-22
how you did about the "need internet explorer" ?

---

