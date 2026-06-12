---
title: "optimize and compress pdf"
date: 2009-06-24
forum: General Help
---

### Post by vishnuvardan on 2009-06-24
List out free packages (which provide command line tool) to compress and optimize pdf files.
I used pdftk. That compresses only some kbs.

---

### Post by vishnuvardan on 2009-06-25
plz reply

---

### Post by kaibob on 2009-06-25
> **vishnuvardan said:**
> List out free packages (which provide command line tool) to compress and optimize pdf files.
I used pdftk. That compresses only some kbs.
vishnuvardan

I do not know of any package that will compress and optimize pdf files. The command line I suggested in the following thread will reduce pdf file size, but it does so with some loss in quality.

[http://ubuntuforums.org/showthread.php?t=1133357](http://ubuntuforums.org/showthread.php?t=1133357)

The pertinent setting in the command line is -dPDFSETTINGS. The following site has a table that details the different -dPDFSETTINGS and what they do:

[http://pages.cs.wisc.edu/~ghost/doc/cvs/Ps2pdf.htm](http://pages.cs.wisc.edu/~ghost/doc/cvs/Ps2pdf.htm)

kaibob

---

### Post by vishnuvardan on 2009-06-29
Thank you very much kaikob
:guitar:It helped me very much.:guitar:

---

### Post by kaibob on 2009-06-29
> **vishnuvardan said:**
> Thank you very much kaikob
:guitar:It helped me very much.:guitar:
Your most welcome. I'm glad that did the job.

---

### Post by hackerb9 on 2010-08-14
> **vishnuvardan said:**
> List out free packages (which provide command line tool) to compress and optimize pdf files.
I used pdftk. That compresses only some kbs.

Debian has released an update to pdftk that compresses correctly as version 1.41+dfsg-9. When next Ubuntu resyncs with Debian, you'll be able to compress PDFs.

---

### Post by Cokaban on 2011-02-02
The best (and the only) free program that i've found myself so far that actually optimises PDF's and can significantly reduce the size without compressing images or any other lossy operations is the[COLOR=Blue] **[PDFCompressor]("http://download.cnet.com/Free-PDF-Compressor/3000-2250_4-10420962.html")** [/COLOR]released in 2005. Apparently newer versions are not free. I run it in WINE to compress PDF files produced by Mac OS Preview application (when merging PDF's or deleting pages in Preview, the size can sometimes increase twice).

---

### Post by KolbenDK on 2011-06-23
There's a nice tool called "Multivalent" on Sourceforge, that has this feature. It's especially useful if you use pdftk to cat a lot of pdf-documents based on the same base document, as it can remove duplicates of images and such in the final document.

It's written in java, and for the past couple of years I've been using it with the following command from the CLI:
java -cp "[Path]\Multivalent.jar tool.pdf.Compress [MyPDFFile]"

It reduces my pdf-file from around 500 MB to 1 MB, as I've concatenated around 500 documents containing the same image as background.

I wish that this feature would be incorporated in pdftk. I don't have the means to do it myself :)

Best regards,
Kolben

---

### Post by MrEgg on 2011-06-27
I came across [this page]("http://howto.landure.fr/gnu-linux/optimiser-un-fichier-pdf-sous-linux") (French) which contains the following method and script. I am not the author of the script and don't deserve any credit for it. I am just translating into English.

First of all, you need to install poppler-utils and ghostscript (most likely, you already have ghostscript) :
```
sudo apt-get install poppler-utils ghostscript
```

Then you need to save the following script :

```
#!/bin/bash

DPI=150
PDF_DESTINATION=""

help() {
echo "optimize_pdf help"
echo "-h : show this help"
echo "-d : (optional) output pdf document resolution, by default : 150"
echo "-s : pdf source file, this file must exist"
echo "-o : pdf output file"
}

full_path() {
if [ -z $1 ]; then
exit;
else
if [ `expr substr ${1:-a} 1 2` != "/" ]; then
FULL_FILE=`pwd`"/"$1
fi
fi
echo $FULL_FILE
}

isNumeric(){ echo "$@" | grep -q -v "[^0-9]" ;}

while getopts "s:o:d:h" flag
do
case $flag in
#Source : source file
"s")
PDF_FILE=`full_path $OPTARG`
if [ ! -e $PDF_FILE ]; then
echo "Please provide a valid source file"
exit=1
fi
;;
#Output : output file
"o")
PDF_DESTINATION=$OPTARG
;;
#Dpi : desired resolution
"d")
if [ -z `isNumeric $OPTARG` ]; then
DPI=$OPTARG
else
echo "Please provide a numeric value for your DPI"
exit=1
fi
;;
"h")
exit=1
;;
esac
done

#Is there a target file?
if [ -z $PDF_DESTINATION ]; then
echo "Please provide a file name for output"
exit=1
fi

#At least one error, we're not going any further
if [ $exit ]; then
help
exit
fi

pdftops \
-paper match \
-nocrop \
-noshrink \
-nocenter \
-level3 \
-q \
"$PDF_FILE" - \
| ps2pdf14 \
-dEmbedAllFonts=true \
-dUseFlateCompression=true \
-dOptimize=true \
-dProcessColorModel=/DeviceRGB \
-dUseCIEColor=true \
-r72 \
-dDownsampleGrayImages=true \
-dGrayImageResolution=$DPI \
-dAutoFilterGrayImages=false \
-dGrayImageDownsampleType=/Bicubic \
-dDownsampleMonoImages=true \
-dMonoImageResolution=$DPI \
-dMonoImageDownsampleType=/Bicubic \
-dDownsampleColorImages=true \
-dColorImageResolution=$DPI \
-dAutoFilterColorImages=false \
-dColorImageDownsampleType=/Bicubic \
-dPDFSETTINGS=/prepress \
- "$PDF_DESTINATION" 
```

Save the script as optimize_pdf.sh, and give it execute permission. Using Terminal, cd to the directory holding your input pdf. To shrink the pdf, type in :

```
/path/to/optimize_pdf.sh -s input.pdf -o output.pdf
```

where input.pdf is the name of your input file and output.pdf the name of your output file. For me, it reduced an original 8-page grayscale document from 4.4M to 1.3M

---

### Post by Cokaban on 2011-06-28
Thanks MrEgg!
I compared the command from the link you have suggested with the PDFCompressor.

A 3.4 MB PDF file was losslessly compressed to 1 MB by the command you've found, and to 2.8 MB by PDFCompressor.exe.

However, i should probably mention that i obtained this test file by removing one page from a 280 KB file with Preview.app, which resulted in a 3.4 MB file.

---

### Post by nilarimogard on 2011-06-28
There's also a Nautilus script to compress PDF files called "[Compress PDF]("http://www.webupd8.org/2010/05/nautilus-script-to-compress-pdf-files.html")".

---

### Post by pterosky on 2012-02-16
Thanks @nilarimogard, I just compressed a 17.7 MB PDF into (drumroll + scary violins) 666 KB, I'm not kidding!

---

### Post by MrOstling on 2013-03-21
You may want to try:

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFOPT -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

The key flag here being -dPDFOPT which optimizes the pdf output.  This command took my 5.1Mb two page color scan down to ~700Kb without a noticeable loss of quality.

---

