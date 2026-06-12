---
title: "Getting firefox to display PDFs in the browser window."
date: 2008-12-24
forum: General Help
---

### Post by MaxIBoy on 2008-12-24
Okay, the problem is this:

I'm trying to use an online textbook. The textbook is a PDF. The problem is that, as an anti-piracy measure, you can only download the front cover and a table of contents that refers to nonexistent files. Essentially, each chapter is mirrored from Glencoe's website, and when you try to go to a chapter, it looks for that mirror.

Their FAQ explains it pretty well:
[http://www.epgtech.com/faqs/Glencoe/OnlineStuEd.htm](http://www.epgtech.com/faqs/Glencoe/OnlineStuEd.htm)


The problem is that I can't get Firefox to display the "main page/table of contents" PDF in a browser window. My only choice is to download the PDF, then open it locally. Then, the viewer I use (be it Adobe's, or Evince, or OpenOffice, or whatever) looks for the mirrored chapters on my hard drive. 

How do I get my web browser to embed the PDF? Back in my Windows days, Minefield did this without complaining.

---

### Post by dcstar on 2008-12-24
> **MaxIBoy said:**
> Okay, the problem is this:

I'm trying to use an online textbook. The textbook is a PDF. The problem is that, as an anti-piracy measure, you can only download the front cover and a table of contents that refers to nonexistent files. Essentially, each chapter is mirrored from Glencoe's website, and when you try to go to a chapter, it looks for that mirror.

Their FAQ explains it pretty well:
[http://www.epgtech.com/faqs/Glencoe/OnlineStuEd.htm](http://www.epgtech.com/faqs/Glencoe/OnlineStuEd.htm)


The problem is that I can't get Firefox to display the "main page/table of contents" PDF in a browser window. My only choice is to download the PDF, then open it locally. Then, the viewer I use (be it Adobe's, or Evince, or OpenOffice, or whatever) looks for the mirrored chapters on my hard drive. 

How do I get my web browser to embed the PDF? Back in my Windows days, Minefield did this without complaining.

Is this any use:

[https://addons.mozilla.org/en-US/firefox/addon/636](https://addons.mozilla.org/en-US/firefox/addon/636)

or:

[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html)

---

### Post by Zill on 2008-12-24
Install [mozplugger]("http://mozplugger.mozdev.org/"):
```
sudo apt-get install mozplugger
```

Test with [http://kb.mozillazine.org/Testing_plugins]("http://kb.mozillazine.org/Testing_plugins")

---

### Post by MaxIBoy on 2008-12-24
Mozplugger helped. It sort of works now. Evince pops up with an "unknown MIME type" message whenever I click on a chapter (and yes, I did set firefox as the default program to open PDFs.)

---

### Post by Zill on 2008-12-25
What happens when you use the test link I supplied?
[URL="http://kb.mozillazine.org/Testing_plugins"]
http://kb.mozillazine.org/Testing_plugins[/URL]

If everything is installed correctly then this should confirm that embedded pdf is working with the message "Your PDF viewing software works!".

If you *do* see this message then it looks like there is a problem with the website document.

---

### Post by MaxIBoy on 2008-12-25
I can view embedded PDFs, but the PDF I'm specifically viewing has a table of contents that links to entirely separate PDFs. These separate PDFs open in Evince, even after Firefox has been set as the default program to open PDFs. Evince apparently can't handle these separate files, giving an "unknown MIME type" error. I suspect that this might not be standards-compliant behavior.


Firefox on my parent's Windows XP computer can handle this just fine. On WINE, the Windows version of Adobe's PDF reader (I tested both version 9 and version 7) causes the windows version of Firefox to lock up, requiring an X restart.


EDIT: The "mother ship" PDF, the one with links to all the separate PDFs, is the only one you can actually download. I poked around it with PDFedit, and either I don't understand it, or it's obfuscated *and* I don't understand it.


This is a link to the "sampler" PDF, which is the only one I can legally link to. It's basically the "mother ship" PDF with the actual links disabled. Still, it might help you to understand what I'm talking about. 
[http://www.glencoe.com/sec/socialstudies/ose/gwhmt/sample/ISEOpen.pdf](http://www.glencoe.com/sec/socialstudies/ose/gwhmt/sample/ISEOpen.pdf)

---

### Post by MaxIBoy on 2008-12-25
I can see the chapters by pulling them up on my parents' machine, then emailing the URL to myself and typing it in after logging into the student textbook access account. They are, in fact, legit PDFs, and I can download and save them. 

Very odd.

---

### Post by Zill on 2008-12-25
> **MaxIBoy said:**
> ...This is a link to the "sampler" PDF, which is the only one I can legally link to. It's basically the "mother ship" PDF with the actual links disabled. Still, it might help you to understand what I'm talking about. 
[http://www.glencoe.com/sec/socialstudies/ose/gwhmt/sample/ISEOpen.pdf](http://www.glencoe.com/sec/socialstudies/ose/gwhmt/sample/ISEOpen.pdf)
If I click on this link then Evince opens up with a single "World History" page containing a single hyperlink labelled "Contents".  Unfortunately, when I click on this link in Evince then nothing happens!

So, at this point I don't really understand what is going on - maybe someone more knowledgeable can throw some light on this. :-)  Good luck.

---

### Post by MaxIBoy on 2008-12-25
Like I said, that's the "sampler." That link is a "free trial," it's the only page I can legally show you guys. 

In the full version, the table of contents brings up other separate PDFs, which don't work on Ubuntu but do work on XP. I can also manually find the URLs of the separate chapters and pull them up on Ubuntu, but I can't get to them by the table of contents. Nor can I locate the URLs of the chapters by the table of contents. I must pull up the chapters on XP, and email the URLs to myself so I can view the chapters on my own computers. It's a major pain. 


Does that make sense? It's a little complicated.

---

