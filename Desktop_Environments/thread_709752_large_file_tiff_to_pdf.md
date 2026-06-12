---
title: "large file tiff to pdf"
date: 2008-02-27
forum: Desktop Environments
---

### Post by mojogil on 2008-02-27
Hello,
I work in the medical construction field. I get a lot of digital blueprints in tiff format.  They show up as 16800x12000. I need to be able to convert to pdf while maintaining the large image size.  I've done it with pdf creator in windows xp (work laptop) but it makes an 8x10 out of it.  
I'm not opposed to purchasing something but I can't let myself fork out the $ for Adobe!
Thank you,
Gil

---

### Post by 50words on 2008-02-27
It may be difficult. PDF converters work by printing the file. Have you tried PDF Edit? Or even just printing to PDF in Ubuntu with a custom document size?

---

### Post by Mr. C. on 2008-02-27
I'm curious.  What is the reason for converting into PDF ?  You have an image file, and you're pushing it into an encapsulating container format which essentially contains the image file data.  Are you just looking to add  Metadata, or don't have a viewer for certain image types on your platforms ?

MrC

---

### Post by mojogil on 2008-02-27
Thank you for the replies.  Maybe there is a better way than converting to pdf.  My problem is that no matter what I use to open the tiff file, it is very slow.  I even tried it in GIMP and it was mega slow.  The program that runs the quickest is the document viewer in microsoft office and it even runs slow. I need the ability to navigate between drawings quickly and expand the view to print out the current view.  I also need it to be large so I can print out the whole blueprint if need be.
Thank you,
Gil

---

### Post by Mr. C. on 2008-02-27
You definitely do not want to create a PDF out of this.

What is the DPI of the TIFF file ?  At 180 DPI, that's a very a very large file... like 500M !

Can your conversion be lossly, such as jpg ?
Can you convert to more efficient formats such as png ?  The same size png is only 80M.

Editing programs will be *much* slower than display-only programs.

Plenty of png viewers to choose from: [http://www.libpng.org/pub/png/pngapvw.html](http://www.libpng.org/pub/png/pngapvw.html)

I don't have any particular recommendation for any of them.  Search google for windows fast png viewer if you are viewing on Windows.

MrC

---

### Post by 50words on 2008-02-27
OF COURSE IT IS GOING TO BE SLOW! Your files are 16800x12000. That is enormous! Changing to PDF won't solve that. If anything, it will slow things down.

The only thing that will make them faster is to make them smaller.

---

### Post by Patb on 2008-02-28
> **mojogil said:**
> Maybe there is a better way than converting to pdf.
Yes. Very likely.  Forget Adobe for the moment. ;)

> **mojogil said:**
>  I need the ability to navigate between drawings quickly and expand the view to print out the current view.  I also need it to be large so I can print out the whole blueprint if need be.
Gil, what is the physical size of the largest printout you want? And what printed dpi do you think you might want? It sounds like 150 dpi might be okay. When you say "blueprint" would just two colours be sufficient? 

For what it is worth, I follow the following steps to deal with large tiff files of scanned documents to reduce the file size for emailing. 
1.  Open the original image in a simple graphics editor - I use Irfanview in Windows or Xnview in Linux.
2.  Resize the image pixel size to about 1600 x 1200 pixels (using Lanczos filter for better quality but it's not critical).
3.  Decrease the colour depth to 2 colours (BW) or 4 greyscale. 
4.  Save as a png file.

This should produce a readable copy of the original document. 

Hope this helps.  Cheers, Pat.

---

### Post by mojogil on 2008-02-28
Thanks for the info Patb,
The output size I want is 30x42 inches.  I looked at the tiff files and they are around 3 mb in size and the page size is listed as 16800x12000.  There is only white background and varying degrees of black lines.  I have since converted some of them to pdf using pdf creator in windows.  I found a way to print to a 30x42 inch pdf.  I don't know why but the pdf files average around 5 mb.  For some reason, the pdf's perform way faster than the tiff files? At first the pdf was reversed in color (black background and white lines).  I don't know why this was but I changed the setting to greyscale and it seemed to work.
I don't understand this stuff very well but what I've done seems to work.

Like I mentioned before, the pdf file allows me to print out (at work) a full size copy of the original that is to scale.  Very important when building a hospital.  It also allows me to just expand small areas and print the "current view" when I only need an 8x10 to hand out.
 Would you have done this differently to achieve a similar result?
Thank you,
Gil

---

### Post by Patb on 2008-03-01
> **mojogil said:**
> Thanks for the info Patb,
The output size I want is 30x42 inches.  I looked at the tiff files and they are around 3 mb in size and the page size is listed as 16800x12000...
Gil

Hi Gil.  I would guess the tiff files are compressed.  I'm surprised the pdf files average as little as 5 mb because as pointed out by Mr C, the pdf format basically contains all the image file data.  

But setting that aside, the image size (in pixels) seems considerably more than you require for a print size of 30 x 42 inches.  Could I suggest you try resizing the tiff file to about half, ie 8,400 x 6,000 pixels.  That should reduce your file size by 75% and yet, at more than 150 dpi, the print quality should still be adequate (unless your hospital builders have very good eyes ;)).  

I don't use the document viewer in MS Office so I can't help you there.  If you use Irfanview, it has a handy 50% button in the resize dialog box.  I'm also not familiar with the use of pdf creator in Windows (Is this beginning to sound like the blind leading the blind? :)) but you may have to adjust the printed dpi setting somewhere to ensure the printout is 30 x 42 inches.  

Good luck.  Let us know how it goes.  

Cheers, Pat.

---

### Post by baxterdog on 2008-03-01
Yep, I've gotten tiff's for DOT plans when we've done some installs and ran into the same problems. Back then I was using windows too.

What I did then was open in photoshop and change the dpi or rescale the imagesize and save as a bmp. (I would use png now)

Insert into an openoffice file and then export directly as a pdf might work for what you're looking for. I understand the print problems too. I've got coworkers who just downgraded to vista and need to view the files I send them, so pdf is still the best option.

---

### Post by stani on 2008-03-03
Hi,

Probably Phatch can solve this issue. You can make an action list which:
- first saves the tiff as a pdf (save in folder "<folder>_pdf/<subfolder>")
- second resizes the image to a smaller size and save as a jpg for quick viewing (save in folder "<folder>_jpg/<subfolder>")

You only need to make the action list once and to save it. Afterwards Phatch can run it on any (folder) you wish and you can get a coffee or some sleep ;-)

You can grab an ubuntu installer at:
[http://photobatch.stani.be](http://photobatch.stani.be) (see free download link below)

Phatch will be available from universe in Ubuntu Hardy.

Let me know if it works for you.

Stani

---

