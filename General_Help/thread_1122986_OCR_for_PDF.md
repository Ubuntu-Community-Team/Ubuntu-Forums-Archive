---
title: "OCR for PDF"
date: 2009-04-11
forum: General Help
---

### Post by michael_miceli on 2009-04-11
I know there are many OCR (optical character recognition) readers out there - clara, tesseract - but is there a feature that will ocr a pdf and then create the same pdf that is now searchable?

Thanks,
Michael

---

### Post by coffeecat on 2009-04-11
Excuse me if I have not properly understood you, but do you mean search a pdf for a word or string? If you do, you don't have to ocr it. Simply open the pdf in Evince (Document Viewer) and File > Find.

If you find Evince too basic, have a look at Okular. It's in the Ubuntu repositories and is an excellent pdf reader. Also with a search function, and a very useful select, copy and paste, which means you could copy and paste the text out into a word-processor.

---

### Post by michael_miceli on 2009-04-11
Sorry for being vague.  I have a pdf that is a scanned image.  It has a lot of text in it; however, it is unsearchable due to the way it was created (scanned).  I was wondering if there was a ocr that would recognize the text to make the same pdf searchable.
Thanks

---

### Post by coffeecat on 2009-04-11
Yes, I see what you mean. It's basically just an image, which happens to have been saved as a pdf. The only way I can think of doing it is to use ocr to read the text, import the ocr text file into something like OpenOffice, reformat the text to look as near as possible to the original pdf, and from OpenOffice save as a PDF by: File > Export as PDF.

Which is very roundabout and not very satisfactory, but it would work. But if you don't want the reconstructed pdf to look exactly like the original, it might be feasible.

---

### Post by michael_miceli on 2009-04-11
Ok thank you,
I guess it is the way PDF's are saved.  There is no metadata inside a PDF file format for text on this page.  I guess it'd be really hard because it'd have to know the pixel position of that specific text.
Thanks again,
Michael

---

### Post by lewelma on 2009-11-14
I, too, am looking for a suitable replacement for Adobe Acrobat Professional. I have a number of PDF articles that are images, and am interested in converting them to Searchable PDF/A format. 

In a Searchable PDF, the OCR'd text resides in the PDF (as a sort of hidden layer), allowing you to search or copy the text out of your image. A search will find the key phrase and highlight it on your image (coffee stains and all). My requirement is that I want to fully index the body text of said articles to help locate the articles using body text search in Zotero.

My current options are: to copy all of my non-searchable PDFs onto a thumb drive and locate a Windows box with Acrobat Professional installed on it. Run the conversion utility, and bring the shiny new Searchable PDF/A files back to Ubuntu.

This is a reliance on Adobe and Microsoft that I would rather not have.

Suggestions anyone???

---

### Post by tlcstat on 2009-12-05
Greetings,
The program that you are looking for is called "Tracker". It has simple settings, but you can designate the size of your index file, Point it to preferred directories etc. You will have to reboot for the indexing to start. The search box will locate your desired text with the paragraph that it is contained in, in the side bar. Very nice. I'm not sure what all I installed to get it to work but you can post if you have a problem and i will check it out. I am a new Linux user myself, but have been able to get just about everything I need working as good or better than Windows. 
tlcstat

---

### Post by sybille on 2009-12-07
Hi, 

Tesseract-ocr does a very good job. I use it frequently, with multiple languages.

Tesseract-ocr can be used from the command line, but I generally use gscan2pdf, which is a graphical application for creating pdfs.

It is possible to import existing pdfs that contain images (scanned pages) into gscan2pdf, then use the ocr feature to convert the image to text. When the pdf is re-saved from gscan2pdf, the scanned text will be included as an annotation. This text will be indexed by Tracker or Beagle, and it can be read in various pdf readers: Okular and the Adobe reader allow the scanned text to be copied and pasted; in Evince, aka Document Viewer in gnome, the scanned text appears as a tooltip and can't be copied.

At present, the gscan2pdf does not match up the ocr text layer with the scanned image of the page, so it's not that helpful for text searching (as opposed to indexing with Tracker, etc.). When searching, your pdf reader will tell you if a word is found on a given page but it won't show you the position on the page. However, the next version of gscan2pdf should include the possibility of saving the ocr with layout using Ocropus, which is a tool related to tesseract-ocr. 

You can follow developments at the sourceforge page and the developer also has a personal package archive (ppa) for Ubuntu where you can find new releases (there aren't any releases for Karmic yet, so it won't be useful to add the ppa to your software sources until there is a new release).

[http://sourceforge.net/projects/gscan2pdf/](http://sourceforge.net/projects/gscan2pdf/)
[https://launchpad.net/~jeffreyratcliffe/+archive/ppa](https://launchpad.net/~jeffreyratcliffe/+archive/ppa)

In any case, gscan2pdf is a really excellent tool if you do any scanning yourself, and it's a very serviceable frontend for adding an ocr text layer to existing pdfs.

---

### Post by nerdelicious on 2009-12-29
Thanks for the detailed info, sybille, you've helped me a lot.

FYI, I just installed gscan2pdf (v.0.9.29-1) on 64-bit Karmic via the Ubuntu Software Center, so it seems to be in the Karmic repos.

BTW, where did you get this information about  the next version of gscan2pdf including the possibility of saving the ocr with layout using Ocropus? I can't seem to find a gscan2pdf roadmap, and this would really be something to be excited about.

---

### Post by sybille on 2009-12-29
> **nerdelicious said:**
> BTW, where did you get this information about  the next version of gscan2pdf including the possibility of saving the ocr with layout using Ocropus? I can't seem to find a gscan2pdf roadmap, and this would really be something to be excited about.

The developer has mentioned this, for example in the following [message from the gscan2pdf help forum]("http://sourceforge.net/mailarchive/message.php?msg_name=30e395780905081256g1133dbe4p3208bc946d91873b%40mail.gmail.com") on SourceForge:
> 
Tesseract does not do layout analysis. However, I have just added support for Ocropus. The text is then recognised and passed to gscan2pdf with bounding boxes, allowing gscan2pdf to place the text in the correct position behind the scan.

This will be in the next release.


Ocropus is already listed as a dependency on the [homepage for gscan2pdf]("http://gscan2pdf.sourceforge.net/").

You'd only need the ppa if you'd like to upgrade to the new version once it is released. Until then, the regular repositories are fine, as you've discovered.

---

### Post by nerdelicious on 2009-12-31
That's great. One of the main reasons I still dual-boot WinXP is the fact I haven't found a Linux-based alternative for Abbyy PDF Transformer. Gscan2pdf sure looks promising.

---

### Post by Koppie on 2010-02-11
Gscan2pdf is GREAT.  It installs pretty much every package you need at once, although I also had to install the tesseract English module.

---

### Post by zztak on 2010-04-08
You might also be interested in the FIRe-text extension for Firefox.  It includes a great guide for converting a pdf to a series of png images and then performing OCR on them using ocropus.  You can then edit the resulting text files using FIRe-text.

[https://addons.mozilla.org/en-US/firefox/addon/11747](https://addons.mozilla.org/en-US/firefox/addon/11747)

---

