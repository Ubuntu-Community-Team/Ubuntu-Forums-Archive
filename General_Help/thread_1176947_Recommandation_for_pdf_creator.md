---
title: "Recommandation for pdf creator"
date: 2009-06-02
forum: General Help
---

### Post by colau on 2009-06-02
Hi,
Which pdf creator software do you recommend for linux?

---

### Post by LepeKaname on 2009-06-02
I use OpenOffice or cups-pdf to create pdf documents... but maybe it is not what you want...

---

### Post by kaibob on 2009-06-02
Have you tried cups-pdf? It's in the repo's and can be installed with the Synaptic Package Manager. You may have to manually create the PDF directory in your home directory.

---

### Post by colau on 2009-06-02
> **kaibob said:**
> Have you tried cups-pdf? It's in the repo's and can be installed with the Synaptic Package Manager. You may have to manually create the PDF directory in your home directory.
Just installed cups-pdf.
Would you please tell how to use it?
I tried this
```

cups-pdf temp.txt t.pdf
bash: cups-pdf: command not found

```

---

### Post by michy99 on 2009-06-02
Open the file in a text editor or word processor. Print. Choose Print to file. Choose .pdf. Enter filename. Print.

---

### Post by colau on 2009-06-02
> **michy99 said:**
> Open the file in a text editor or word processor. Print. Choose Print to file. Choose .pdf. Enter filename. Print.
Thanks.
Is there any graphical software to convert any files info pdf?

---

### Post by mikeize on 2009-06-02
eh?  That IS a graphical way to create pdf files...

---

### Post by kaibob on 2009-06-02
> **colau said:**
> Just installed cups-pdf.
Would you please tell how to use it?
I tried this
```

cups-pdf temp.txt t.pdf
bash: cups-pdf: command not found

```

Cups-pdf is installed as a print driver. So, load the document in whatever application you are using and open the print dialog (normally File > Print). Then select the PDF printer (see the screenshot below). 

As an aside, the method mentioned by michy99 is different from cups-pdf. The method used is one of personal preference.

---

### Post by colau on 2009-06-02
> **kaibob said:**
> Cups-pdf is installed as a print driver. So, load the document in whatever application you are using and open the print dialog (normally File > Print). Then select the PDF printer (see the screenshot below). 

As an aside, the method mentioned by michy99 is different from cups-pdf. The method used is one of personal preference.
Thanks.
So without these methods from File>Print, there is no other way(seperate single software) to do this conversion?

---

### Post by ad_267 on 2009-06-02
You can use OpenOffice to export files as PDF. Scribus is good application for generating PDFs for brochures and newsletters etc. What exactly are you trying to do? Do you just want to convert plain text documents to PDF?

---

### Post by DeMus on 2009-06-02
> **ad_267 said:**
> You can use OpenOffice to export files as PDF. Scribus is good application for generating PDFs for brochures and newsletters etc. What exactly are you trying to do? Do you just want to convert plain text documents to PDF?

Or do you need intelligent pdf files like you can make with Adobe pdf writer? Files with build-in links to other pages, etc?
When using the printer method you get a simple pdf file, good quality to read but no intelligence.

---

### Post by colau on 2009-06-02
> **ad_267 said:**
> You can use OpenOffice to export files as PDF. Scribus is good application for generating PDFs for brochures and newsletters etc. What exactly are you trying to do? Do you just want to convert plain text documents to PDF?
Thanks for your reply.
Actually I am searching for a graphical software which can convert any format into pdf.

---

### Post by colau on 2009-06-02
> **DeMus said:**
> Or do you need intelligent pdf files like you can make with Adobe pdf writer? Files with build-in links to other pages, etc?
When using the printer method you get a simple pdf file, good quality to read but no intelligence.
Yes, like Adobe Acrobat 6.

---

### Post by kaibob on 2009-06-02
> **colau said:**
> Thanks.
So without these methods from File>Print, there is no other way(seperate single software) to do this conversion?
In addition to the programs mentioned by ad_267, there are command-line utilities that will convert many documents and images to PDF format. If you are looking for one program with a graphical interface that will convert all file formats to PDF format, I'm not aware of one.

EDIT: There is no direct Linux equivalent to Adobe Acrobat.

---

### Post by colau on 2009-06-02
> **kaibob said:**
> In addition to the programs mentioned by ad_267, there are command-line utilities that will convert many documents and images to PDF format. If you are looking for one program with a graphical interface that will convert all file formats to PDF format, I'm not aware of one.
Ok.
What are those command-line utilities?

---

### Post by kaibob on 2009-06-02
> **colau said:**
> Ok.
What are those command-line utilities?
There are a number of them, but the most comprehensive is the Imagemagick suite of utilities. The following link will take you to a page that lists all of the file formats that Imagemagick can convert to PDF format:

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

---

### Post by Chronon on 2009-06-02
Maybe you will find this application useful: [http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html](http://www.cyberciti.biz/tips/open-source-linux-pdf-writer.html)

I never used it.  I usually just use LaTeX for PDF preparation.  LyX is a sort of WYSIWYG editor that can export LaTeX and therefore also PDF.  I don't know if that would work for you or not.

Edit: That site I linked actually contains several options on it.  Interestingly, one of them is a web application located at: [http://www.pdfescape.com/](http://www.pdfescape.com/)

---

### Post by starcannon on 2009-06-02
PdfEdit is a great program.

Synaptic Package Manager: Search: pdfedit

Or to install from terminal
```

sudo apt-get install pdfedit

```

Good GUI that lets you do anything you can think of to a PDF.

Have fun.

---

### Post by Chronon on 2009-06-03
Cool.  That was the main solution offered on the page I linked.  It's nice to hear an endorsement from someone who has used it.

---

### Post by starcannon on 2009-06-03
> **Chronon said:**
> Cool.  That was the main solution offered on the page I linked.  It's nice to hear an endorsement from someone who has used it.
I used it to deal with a bunch of mortgage papers not to long ago, its a nice tool, I like it a lot. One of those things I could never have afforded in the other OS.

---

### Post by colau on 2009-06-03
> **kaibob said:**
> There are a number of them, but the most comprehensive is the Imagemagick suite of utilities. The following link will take you to a page that lists all of the file formats that Imagemagick can convert to PDF format:

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)
Imagemagick is already installed.
Would you please tell how convert text files into pdf files with imagemagick?
I am googling though.

---

