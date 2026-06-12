---
title: "sane compression issues"
date: 2008-12-07
forum: General Help
---

### Post by x20mar on 2008-12-07
Hi

I finally got my scanner working in Ubuntu, however I'm having file compression issues.

For example, a 3 page PDF document would be produced with a file size between 30 and 50MB, where an equivalent file made on a windows platform would be less than 1MB!

I narrowed this down to the fact that it's scanning each page with an estimate of 25.5MB per file.

Any tips in fixing this as a file between 30 and 50MB isn't e-mailable (wow that's actually a word).

Thanks

PS. if it's any help my scanner is an Epson 4490

---

### Post by Tamlynmac on 2008-12-08
One thing that may help is you to lower your scanning resolution.

For example: For my HP scanner I use a resolution of 300 dpi for text and most pdf's with fairly good results. Full page at 300dpi text is about 4 meg. Reducing the res will reduce the file size.

Of course color images may require significantly higher res for quality scanning.

---

### Post by x20mar on 2008-12-08
Hi

Thanks for getting back to me. As far as sane (or xsane in this case) the scan is set to 300dpi so I don't think that's the problem.

Any other suggestions?

Thanks

---

### Post by scorp123 on 2008-12-08
> **x20mar said:**
> For example, a 3 page PDF document would be produced with a file size between 30 and 50MB  Check your PDF export settings. There are various settings regarding "target media". If you set it to "Printing" then it is assumed that you need extra high resolution and the files get perversly big. If you set the setting to "Screen" then the files get really small. Also: you can tweak the compression algorithm. I use JPEG compression (set to 90%) and the quality I get is tip top. And yet the files don't get too big.

---

### Post by x20mar on 2008-12-08
Hi Scorp,

Where abouts do you edit the settings for the target media?

Thanks

---

### Post by Slim Odds on 2008-12-08
It sounds like you are mixing apples and oranges.

How was the "windows" PDF created?

A PDF file can contains many things. Text, graphics, etc.

If you scan a page to create an image and then stick that in a PDF file, it will be large.

If you scan a page using OCR to convert to text and then stick that in a PDF file, it will be much smaller.

---

### Post by x20mar on 2008-12-08
When I mean "windows" created, I mean using the windows software provided for the scanner by epson. No ocr is used at all

---

### Post by Slim Odds on 2008-12-08
> **x20mar said:**
> When I mean "windows" created, I mean using the windows software provided for the scanner by epson. No ocr is used at all

I guarantee that if the output file size is <1MB for a 3 page document, there's some OCR involved.

Open the file in a text editor and take a look at it.

---

