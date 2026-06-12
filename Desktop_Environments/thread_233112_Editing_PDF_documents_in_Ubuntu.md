---
title: "Editing PDF documents in Ubuntu"
date: 2006-08-09
forum: Desktop Environments
---

### Post by jlhughes on 2006-08-09
On my Mac I have purchased the Adobe Acrobat Professional software so that I can edit PDF documents -- insert pages, delete pages, merge PDF documents, etc. (I'm NOT talking about editing the text of the PDF document.)

Is there an application that runs in Ubunutu/Gnome that has this ability?

Thanks

---

### Post by sfabel on 2006-08-10
I don't know any specifics regarding features, but both OpenOffice Writer and KWord come with PDF support.

KWord can open and edit PDF documents just as if they were "normal" Documents. I haven't used it much, so really you'd need to test it first if it suits your needs.

Cheers,
Stephan

---

### Post by jlhughes on 2006-08-10
> **sfabel said:**
> I don't know any specifics regarding features, but both OpenOffice Writer and KWord come with PDF support.

KWord can open and edit PDF documents just as if they were "normal" Documents. I haven't used it much, so really you'd need to test it first if it suits your needs.

The specific issue is this case is filling out a job application designed in Word (this part works in OpenOffice fine).  I output the entire document to PDF (again OpenOffice does this). I then print the signature page. Sign the signature page. Scan the page. Output the scan as a PDF page.  Delete unsigned page from the full document. Insert the signed page.

I don't think editors will be the answer. AbiWord opens the document and displays all of the UNFORMATTED text and doesn't pick up the Word tag fields that I filled out.  

While writing this response, it occurred to me that I could scan the signature portion of the form and then insert the image of the signature into the document and then output the whole thing to PDF. That's obviously a simple alternative.

But I would still like to be able to delete and insert  PDF pages and merge PDF documents.

---

### Post by LxP on 2007-01-28
Check out the pdfjam package.  It allows you to join PDFs together (specifying which pages should go into the output file), so you could join all but the last page of the original PDF with the separate signed page PDF.

---

### Post by mexlinux on 2007-01-28
[http://www.kde-apps.org/content/show.php?content=37321](http://www.kde-apps.org/content/show.php?content=37321)

---

### Post by dustrho on 2007-07-25
Any other suggestions on how to edit a PDF document? I'd like to be able to at least create custom bookmarks and add notes to any PDF document.

Thanks.

---

### Post by jetpeach on 2007-07-27
this has been the most frustrating thing for me in my years on linux, and the number 1 reason i have to keep windows (and boot it).  i am a grad student and need the ability to highlight PDFs and add notes, so when i look back at the literature i've been reading i can remember it better... people never understand how essential this can be (what's wrong with reader? or try openoffice..." - these solutions have not worked at all for me since they pretty much destroy the pdf formatting half the time...)

so i've been trying to get acrobat professsional to work using wine. apparently others have been successful
[http://appdb.winehq.org/appview.php?iVersionId=4922](http://appdb.winehq.org/appview.php?iVersionId=4922)
but for me i get it to load and everything, but then it quits after about 10 seconds.  i can even see the beautiful file loaded and interact for a second with it...but alas, no success for me yet.  but if any of you know a thing or two about programming, please post your experience on the page linked about and try to help the wine developers - they are really awesome and are soo close to having acrobat prof. work (6 months ago you couldn't even install it, now all those bugs are fixed), i really hope to have this as a solutions in the next few months.

okular is my other hope for this solution
[http://okular.kde.org/formats.php](http://okular.kde.org/formats.php)
it is kde's universal document "viewer" but as you can see they are saying some basic highlighting and pdf manipulation should also be possible in it. hopefully kde4 (and okular) will come sooner rather than later!

---

### Post by philten on 2007-07-28
As of yet, there are very few options for editing PDF's in Linux. Currently, two programs are out there that allow for very basic manipulation of PDF's:

1) flpsed - This program only allows for the addition of text, and is made to operate on PS's not PDF's although PDF's can be easily converted using $pdftops (I have found this to proved better bounding boxes than $pdf2ps). In general this program is rather unsatisfactory and not worth trying.

2) pdfedit - This program has a few more frills and allows for various things like the addition of highlighting, etc. but in general I still find it be very limited. A large problem that I ran into was the inability to type landscape text over a landscape oriented PDF. Again, this program has a lot of problems, including the inability to re-edit text, etc.

Neither of these programs allowed me to type landscape text on a landscape PDF form that I was trying to fill out, which frustrated me to no end. To get around this I realized that oodraw can easily handle EPS files without loss of quality. Using $pdftops and $ps2eps one can create an OpenOffice drawing and type whatever over the EPS image from the PDF, and save, without loss of quality. Of course, saving as PDF again is simple because of OpenOffices built in support. The only problem that I ran into was that ps2eps would print multiple pages to one EPS file. To get around this I wrote this little script that automates the entire process. To get it to run you need to have OpenOffice installed, along with pdftops (not pdf2ps, again bounding problems), and ps2eps (not ps2epsi, this is a format that OpenOffice cannot handle).

--------------------------------------------------------------------------------------------------------------------------------

#!/bin/bash
# This script takes a pdf file, finds the number of pages, converts each page
# individually into a ps using pdftops. Each ps file is then converted to an
# eps file using ps2eps, and the subsequent page is opened with oodraw for ed-
# iting purposes without loss.

PAGES=`pdfinfo $1 | grep "Pages" | awk '{ print $2 }'`
echo $PAGES "page(s) found in file."
echo "Converting to PS format."
COUNTER=1
while [  $COUNTER -le $PAGES ]; do
     pdftops -f $COUNTER -l $COUNTER $1 tmp$COUNTER.ps
     let COUNTER=COUNTER+1 
done
echo "Succesfully converted to PS, converting to EPS format."
COUNTER=1
while [  $COUNTER -le $PAGES ]; do
     ps2eps tmp$COUNTER.ps
     rm tmp$COUNTER.ps
     let COUNTER=COUNTER+1 
done
echo "Succesfully converted to EPS, opening in OpenOffice Draw for editing."
COUNTER=1
while [  $COUNTER -le $PAGES ]; do
     oodraw tmp$COUNTER.eps
     let COUNTER=COUNTER+1 
done
echo "Cleaning up ..."
sleep 20
COUNTER=1
while [  $COUNTER -le $PAGES ]; do
     rm tmp$COUNTER.eps
     let COUNTER=COUNTER+1 
done

--------------------------------------------------------------------------------------------------------------------------------

I hope this helps someone out there, it has certainly proved rather useful to me. Highlighting of course can be done within OpenOffice using a fill that is semi-transparent, and while this is not ideal, it still works. This certainly is not a method that I would use for editing actual documents, but is very useful for filling out forms, etc.

-- philten

---

### Post by ramjet_1953 on 2007-07-29
pdfedit is available from getdeb

[http://www.getdeb.net/](http://www.getdeb.net/)

Regards,
Roger :cool:

---

