---
title: "Ebook Maker?"
date: 2009-03-03
forum: Education &amp; Science
---

### Post by babujbf on 2009-03-03
Im in a hurry, my college teacher asked me to scan a document of about 10 pages and make it into a pdf. Like if it was a pdf ebook. How can I do this with ubuntu? What do I need?

---

### Post by babujbf on 2009-03-03
Im in a hurry, my college teacher asked me to scan a document of about 10 pages and make it into a pdf. Like if it was a pdf ebook. How can I do this with ubuntu? What do I need?

---

### Post by tgalati4 on 2009-03-03
In a terminal:

>man sane

What type of scanners do you have access to?

OpenOffice can handle the formatting and PDF export after scanning.

---

### Post by babujbf on 2009-03-03
I already got the scanned pages, I just need to convert them all into one pdf ebook type file. I have them all on separate .jpg. I'm also running on hardy.

---

### Post by earlycj5 on 2009-03-03
You can do this with Ubuntu.

Are you asking how to scan, or create PDFs or both?

Basically I'd scan the files, save as a .tiff and convert to a .pdf format.

See this thread: [http://ubuntuforums.org/showthread.php?t=114568](http://ubuntuforums.org/showthread.php?t=114568)

---

### Post by kaspar_silas on 2009-03-03
> **babujbf said:**
> Im in a hurry, my college teacher asked me to scan a document of about 10 pages and make it into a pdf. Like if it was a pdf ebook. How can I do this with ubuntu? What do I need?

Scan each page and save it as a .TIFF / .JPG file or whatever the type doesn't matter.

Install imagemagick using synatic [it's in the repositories] 

open a terminal and cd to the directory with the images. Then type 

$ convert *.jpg -adjoin ebook.pdf

you can change .jpg to almost any image format. Or if you have lots of other images files in the folder just specify the ones you want by name.

$ convert 1.jpg 2.jpg 3.jpg -adjoin ebook.pdf

the output ebook is a multi page pdf.

---

### Post by tgalati4 on 2009-03-03
Using OpenOffice 2.3:

Open Writer:

Insert-->Picture-->From File-->Choose *.jpg file for first page.
Go to second page in Writer
Repeat insert for rest of pages.
Format as necessary
File-->Export as PDF-->pick a meaningful filename to save
Open your new pdf using acroread or evince to see if it is readable.

---

### Post by kayosiii on 2009-03-03
Scribus probably produces the best quality pdf output on the linux platform.... Similar deal to what happens in OOo above

---

### Post by earlycj5 on 2009-03-03
Didn't I answer this in another section of the forum or am I dreaming?

---

### Post by Dragonbite on 2009-03-04
Anybody try Okular? It's a KDE 4.x application but I'm curious if it is able to do this or not.

---

### Post by lykwydchykyn on 2009-03-04
Okular is mainly just a viewer, I'm not aware that it's indended for actually creating PDFs.

---

### Post by kleeman on 2009-03-05
Use xsane to scan the ten pages. It has a multipage pdf output option.

---

### Post by ssam on 2009-03-05
[gscan2pdf]("http://gscan2pdf.sourceforge.net/") looks to be just what you want. i assume it is in the repos.

--
PS: it can be considered rude to post a message in 2 forums ( [http://ubuntuforums.org/showthread.php?t=1085931](http://ubuntuforums.org/showthread.php?t=1085931) ). the forum code of conduct says "Please do not cross post, or post the same thing in multiple locations." [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

