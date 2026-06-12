---
title: "Note taking and Organization Software"
date: 2006-07-28
forum: Desktop Environments
---

### Post by mattyh on 2006-07-28
Quick Rundown:

 I'm looking for software that will allow me to organize notes I will be taking during law school (starting in 3 weeks :-& ).  Unfortunately, I haven't really been able to find anything that great.  Ideally, I would use something that would allow me to store pdfs and text documents (in whatever format) within some sort of hierarchy.  I'm assuming I will scan handouts/cases into pdf and I'm leaning towards taking notes by hand and either scanning or retyping them (depending on content).

 I'm hoping someone out there has used software for this very thing, or has some software in mind.

 Thanks in advance,
 Matthew

---

### Post by djdennie on 2006-07-28
I'm not sure if there's specialised software to do this... but you could easily do this just by using some kind of directory structure on the filesystem that you put your plain text and pdf files in.

---

### Post by aysiu on 2006-07-28
Try *kjots* or *gjots2*:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kjots&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kjots&searchon=name&subword=1&version=all&release=all)

---

### Post by drtpw on 2006-07-28
I've been messing with this for a while.  Ubuntu supports xsane-0.97 which does not offer the choice of saving a scan to PDF.  However, there is a 0.991 version available that does offer this option.  I have read threads from people saying that this works great but I have had no luck getting it to install and run properly.  However, I am a newbie and that is probably as good an explanation as any.  You can give that a try.

A second option is to scan with 0.97, saving it as a postscript file and sending it to [http://www.ps2pdf.com/convert/convert.htm](http://www.ps2pdf.com/convert/convert.htm)

Another thread says that Kooka can do it but I haven't looked into that.

Third, and what I chose to do is that I have installed a virtual PDF printer instead that is working for me until Ubuntu supports the 0.991 version of Xsane.

The following is from, and thanks to, LoKi128:

Thanks to everyone from this thread for all their guidance. The sticking point in this whole process is that you need to be root to edit the permissions on the executable.

   1. Install the cups-pdf package (I used version 2.2.0-1)
   2. Go to System -> Administration -> Printing
   3. Doubleclick "New Pinter"
   4. Notice that there is no mention of a CUPS PDF printer
   5. Open a terminal and tpe "sudo nautilus" and then your     password
   6. Go to Filesystem -> usr -> lib -> cups -> backend
   7. Rightclick "cups-pdf" and select Properties
   8. Go to the Permissions tab and click the "Set user ID" special flag
   9. Again try to add a new printer
  10. There is now a "PDF Printer" detected, select it
  11. Select the Generic, Postscript Color Printer (Rev 3b)
  12. Give it a name, like PDF Printer
  13. Right click on the newly created printer, and select Properties
  14. Click "Print a Test Page"
  15. The file should be in your Home folder, under the PDF folder

Good luck.  Sorry this is so long.

---

### Post by mattyh on 2006-07-28
I hadn't even fathomed that xsane wouldn't save to pdf.  Good idea with the cups-pdf, I used similar functionality in windows to save receipts from online purchases, etc (internet explorer is possibly the worst app to print from ever, always looks like crap in my experience).

As for the filesystem idea, I figured that is how I would do it unless I could find some software that would help me organize a bit more.  I'm not averse to using that method, and to be honest I'd be happy using gedit or something to take notes, but I was hoping there was something that might allow me to say, scan an image of some diagram from class and add that to the document.  Though, I suppose OpenOffice might suffice for that...

---

### Post by goteetech on 2006-07-28
I have a simpler solution...Simply use OpenOffice Word Processor, to type your notes, and link your other documents or scanned images with the Insert-Picture-Scan function or link pre-existing docs and pdfs with the Insert-HyperLink function, which will allow you to link, websites, web based docs, mail items, docs of various types stored locally on your computer, or create a new document. I have tried several different solutions, including Visualize Your Mind, Tomboy, various desktop and webbased Wiki's, Project Management Tools. If you are stricly looking for a Desktop based solution, OO.org may be the simplest and easiest solution for you...If you have a web server, that opens up a whole new set of apps...

---

### Post by mattyh on 2006-07-28
I found a slashdot article via google in which a lot of poeple talked about setting up a wiki.  Is that really that useful of a solution?  I have no problem getting in depth with this as I was a CS major in undergrad and have toyed around with linux for a while.  Also, I'll have a desktop at home that can be a server if need be.

---

### Post by jstrube on 2006-08-06
Not sure about getting your content into pdf, but for organizing information I use a combination of
tomboy and [Treeline]("http://www.bellz.org/treeline/"). Those two are small.
[BasKet]("http://basket.kde.org/") is a bit more heavywewight, as it needs KDE libraries, but IMHO it's worth it. Check out the beta of BasKet note pads, though. It's much better than the older version.

---

### Post by RikoW on 2006-08-07
> **drtpw said:**
> 
... snip ...
A second option is to scan with 0.97, saving it as a postscript file and sending it to [http://www.ps2pdf.com/convert/convert.htm](http://www.ps2pdf.com/convert/convert.htm)
... snip ...



or you can just use on the command line:

```

ps2pdf input.ps output.pdf

```

Cheers,

             Riko

---

### Post by drtpw on 2006-08-08
Riko,

Thank you.  I can't wait until I learn the language, terminal, and such, better.  I was laughing when I read how simple your command line was.  Someday I'll figure all this out.  Still, I'm faster at this than I was with Windows 2.01

---

### Post by shax on 2006-09-17
Another option is using a personal wiki or wiki-like app, in a way similar to what you would use Microsoft Onenote for. 

[http://wiki.tcl.tk/3747](http://wiki.tcl.tk/3747) or just google 'personal wiki'.

---

