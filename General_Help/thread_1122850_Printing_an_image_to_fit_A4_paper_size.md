---
title: "Printing an image to fit A4 paper size"
date: 2009-04-11
forum: General Help
---

### Post by anc2020 on 2009-04-11
Hi, I'm having a bit of trouble trying to print an image on an A4 sheet of paper.

Using the print menu option from Image Viewer results in a new print queue item, but after a while it says "printer might not be connected".

Alternatively, using the command lp does print the image, but it prints the image with really big margins causing it to be printed over multiple pages. I've tried commands like "lp -l", "lp -o media=a4" and "lp -o page-bottom=0 -o page-left=0 -o page-right=0 -o page-top=0", but none of these cause the image to fit the paper and my bin is starting to fill up!

I've got a color laserjet 2600n set up on Ubuntu 8.10 and can print text documents fine with color. I'm also not very concerned about being able to print using Image Viewer, so if there is a command I can use that would be great.

Hope I've posted to the right place and thanks for any help

---

### Post by hyper_ch on 2009-04-11
if there's too much data to process that message appears some time. If you wait for a while, wil it still print?

---

### Post by anc2020 on 2009-04-11
Thanks yeah it did print after some time.

Do you know of a command I can use to do this?

---

### Post by hyper_ch on 2009-04-11
a command to do what?

---

### Post by anc2020 on 2009-04-11
> **hyper_ch said:**
> a command to do what?

Currently, if I type "lp myfile.png", the image prints, but instead of printing on one sheet, it prints on 4 sheets because it puts a lot of blank space around the sides so it can only a small amount of the picture on each sheet. I've tried a few variations of options on the "lp" command, but with no success.

So basically I'd really like to know a command to print an image to fit an entire A4 sheet, much like printing from Image Viewer would give.

Any ideas?

---

### Post by hyper_ch on 2009-04-11
try the scaling=100 option... not sure if it also downscales.

---

### Post by anc2020 on 2009-04-11
Great it worked, thanks!

Sorry I'm not sure how I missed that...

---

