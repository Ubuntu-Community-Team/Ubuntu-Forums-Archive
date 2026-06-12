---
title: "Watermarks to PDF documents: Is there a simple method?"
date: 2009-03-04
forum: General Help
---

### Post by Pipps on 2009-03-04
I have a PDF file which is a standard typed-up letter in black text on a white background.

I would like to add a watermark to the background of the document. The word 'COPY' in a large, bold, greyed-out text, reading diagonally from 7 o'clock to 1 o'clock in the background.

I have tried countless methods, and have gotten nowhere myself so far.

I therefore refer this matter to the experts. Please let me know how you would perform this task. Thank you!

---

### Post by HermanAB on 2009-03-04
There is a pdf merge utility that can mix two PDFs, provided that they are both created by the same application.  Though I cannot remember the exact name of the thing.

Another way is to add a CUPS pre-filter to print with a watermark and when all else fails, you can use The Gimp.

Cheers,

Herman

---

### Post by stumbleUpon on 2009-03-04
You can use pdfxchangeviewer to add watermarks

See here [http://lglinux.blogspot.com/2008/01/pdf-viewer-with-text-highlighting.html](http://lglinux.blogspot.com/2008/01/pdf-viewer-with-text-highlighting.html)

---

### Post by kaibob on 2009-03-04
You ask for a simple method, and this is not one. But, if all else fails, have a look at the Imagemagick Composite utility:

[http://www.imagemagick.org/script/composite.php](http://www.imagemagick.org/script/composite.php)

[http://www.imagemagick.org/Usage/annotating/#watermarking](http://www.imagemagick.org/Usage/annotating/#watermarking)

---

### Post by Pipps on 2009-03-04
> **stumbleUpon said:**
> You can use pdfxchangeviewer to add watermarks

See here [http://lglinux.blogspot.com/2008/01/pdf-viewer-with-text-highlighting.html](http://lglinux.blogspot.com/2008/01/pdf-viewer-with-text-highlighting.html)

It would appear from the link you provide, that pdfxchangeviewer requires Wine.

This instantly makes it not simple! My Ubuntu system is a Wine-free zone! :P

---

### Post by Pipps on 2009-03-04
> **kaibob said:**
> You ask for a simple method, and this is not one. But, if all else fails, have a look at the Imagemagick Composite utility:

[http://www.imagemagick.org/script/composite.php](http://www.imagemagick.org/script/composite.php)

[http://www.imagemagick.org/Usage/annotating/#watermarking](http://www.imagemagick.org/Usage/annotating/#watermarking)

Thank you for the suggestion. At least there is one proven method!

---

### Post by altonbr on 2009-03-04
I think [Phatch]("http://photobatch.stani.be/") does this. It's a photo program for doing batch editing.

It is available in 8.04, 8.10 and 9.04 (dev).

```
sudo aptitude install phatch
```
or install through synaptic

---

### Post by Pipps on 2009-03-04
I have found a method which is as simple as I would desire:

It's called: [JPDFTweak]("http://sourceforge.net/projects/jpdftweak").

I have set out step-by-step directions, below:

1. Make sure you have Java 5 or higher installed.
   - " *sudo apt-get install sun-java5-jdk* "
2. Download the file called *jpdftweak-0.9.zip* and unzip it.
   - [Right click > 'Extra here'.]
3. Enter the folder, right click on the file called *jpdftweak.jar*, and click 'Open with Java'.

4. Select your input PDF file.
5. Click on the 'Watermarks' tab.
6. Tick 'Add transparent text watermark'.
7. I then enter the text 'C O P Y'.
8. Click on the 'Output' tab.
9. May I suggest, clcik on your original file in the browser, then insert the number '2' at the end, to distinguish it from your input file. Then click ok.
10. Then, click your cursor into the output file path field, and hit 'Enter' on your keyboard.
11. A small dialogue box should indicate that it's worked.

You should be happy with your watermarked PDF file. I certainly am!

Now, I can't possibly think of anything more simple than that!

---

### Post by iaculallad on 2011-09-26
Reviving an old post wouldn't be good but just to add a simple command which will make the post above mine helpful to new Linux users:

Open Terminal (Ctrl+Alt+T) and issue the command below to make it executable before running it with Java:

chmod +x jpdftweak.jar

HTH.

---

### Post by wincliff on 2012-02-25
Thank you so much ! Worked like a charm ! :-) May the source be with you...

---

### Post by oldos2er on 2012-02-25
Closed, necromancy.

---

