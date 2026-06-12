---
title: "Acroread copy/paste"
date: 2006-07-16
forum: Desktop Environments
---

### Post by matt_man22 on 2006-07-16
Anything I copy from Adobe Acrobat is gibberish.  I am using the latest repository version.  This happens with both images and text.  Anyone else running into this problem or know a solution?

---

### Post by aysiu on 2006-07-16
Can you post a link to one of these PDFs, so we can see if it's something with your installation, something with the PDF, or something with the application you're trying to paste into?

By the way, what applications are you trying to paste into? I know GIMP has some issues.

---

### Post by matt_man22 on 2006-07-16
My example is a simple kprinter PDF from slashdot.  I attempted to copy text into openoffice, kedit, and kate to no success.  Then I attempted to copy images into kolourpaint, gimp with no success.  This seems to happen with all PDFs that come from the kprinter.

(I had to select a very small part to fit into the 20k limit).

---

### Post by aysiu on 2006-07-16
Well, same here. When I tried to paste into OpenOffice, I got this: ```
	
 !
	

 !"#!$
%	&''(
"#$%
$
$

$$
$$
$&
$


%
$
$&

$
$%
$
'
()
*

&$
$
&

$)

&$
$
&$+$%


$
$
)


'



$

$
&$$
,

$&	
``` And when I imported the PDF into KWord, none of the words came in--only the picture of the briefcase, hat, and phone came in.

Maybe it has something to do with the character encodings of that PDF? I haven't had troubles like that with other PDFs.

---

### Post by matt_man22 on 2006-07-16
I am using the default kprinter settings for PDF.  I am printing from firefox, so I don't think I really changed something.  This is also my second install of Kubuntu with the same problem.

---

### Post by aysiu on 2006-07-16
I believe it has something to do with the PDF itself and not the programs you're using to view it. Did you create that PDF? I thought you said you got it off Slashdot.

I believe the way it was created--the character encodings that were used during the creation of the PDF--is giving the funny copy/paste output.

---

### Post by matt_man22 on 2006-07-16
It was created by me, through kprinter.  Just using the default settings that come with it.  Only thing I changed was setting firefox to use kprinter.

---

### Post by matt_man22 on 2006-07-16
I tested an existing PDF from a website, and Acrobat does copy and paste correctly.  It does seem to be something with the encoding.  Any way to correct this?

---

### Post by aysiu on 2006-07-16
> **matt_man22 said:**
> I tested an existing PDF from a website, and Acrobat does copy and paste correctly.  It does seem to be something with the encoding.  Any way to correct this?
None that I know of. Someone else on these forums may know how to convert the PDF to text and change the encoding somehow in the process.

---

### Post by matt_man22 on 2006-07-16
Well thanks for your help, hopefully someone else knows something about the encoding.

---

### Post by matt_man22 on 2006-07-16
aysiu,

Would you be able to test printing a PDF from firefox on your system and see if you get similar results?  Thanks.

---

### Post by aysiu on 2006-07-16
> **matt_man22 said:**
> aysiu,

Would you be able to test printing a PDF from firefox on your system and see if you get similar results?  Thanks.
Can you explain a bit what that means? Printing a PDF...?

---

### Post by matt_man22 on 2006-07-16
Well, first you need kdeprint from the repositories.  This comes with the kubuntu-desktop if you have it.  It then installs a printer called "Print To File (PDF)."  You will get this from any KDE application

To have firefox use this printer, simply go to about:config and set the "print.printer_PostScript/default.print_command" to "kprinter." (You may want to back up the old command if you ever want to restore it).  Then print from firefox using the Postscript/Default printer.  A KDE dialog will come up, and then select Print To File (PDF) from the printer name and save it.

---

### Post by aysiu on 2006-07-16
I tried that, but I never get the option to save it as a PDF. It automatically saves as a postscript file.

---

### Post by matt_man22 on 2006-07-16
Did you change the firefox settings in about:config (my last post)?  Firefox needs to be redirected to the kprinter.

---

### Post by matt_man22 on 2006-07-17
If I export a PDF from OpenOffice, it works correctly in Acrobat.  There must be some setting I'm missing in kprinter.  Anyone know the settings of kprinter?

---

### Post by matt_man22 on 2006-07-25
Sorry to bump this, but I still cannot figure out how to get the correct encoding for pdf files with kprinter.  I am really suprised no one else has brought this up.  This problem is off of a standard install.

---

