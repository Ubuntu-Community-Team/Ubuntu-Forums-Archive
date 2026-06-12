---
title: "gnumeric doesn't save .xlsx"
date: 2011-11-06
forum: Desktop Environments
---

### Post by sowdust on 2011-11-06
Hello everyone,

I recently had to modify an .xlsx spreadsheet (created either with an apple or a microsoft application) using Gnumeric.
Once I tried to open it with Microsoft Office it said the file was corrupted and needed to be fixed. It tried to fix it, with no success.
I then tried to open it from open office, save it as an .xls file: this made it readable by Excel.
The strange (to me) things are two:

 - the file contained only numbers,simple formulas (networkdays())         and a line plot
 - the .xls file is about 125kb, while the .xlsx file is 970kb

how is this possible?

---

### Post by maddog39 on 2011-11-06
While I can't speak for Gnumeric, I can say that more than likely, OpenOffice/LibreOffice will give you better results in this type of situation. Also, Microsoft is pretty notorious for chaning the OOXML format ever so slightly in Microsoft Office without telling anybody and causing problems for everyone else who doesn't use Microsoft Office. I would say stick with the older .xls format if you can as well, I've had much better luck personally with the older binary-based formats and OpenOffice than I do with OOXML based documents.

---

### Post by sowdust on 2011-11-07
thank you for your suggestion! What I was very curious about is

- why the same file is 9 times larger if saved as .xlsx than if it's .xls 
- gnumeric doesn't seem to generate very portable files: not only his .xls and .xlsx file cannot be opened by Ms Office, but also Open Office crashes every time I try.

I solved installing open office on my pc and I think I will use that one from now on, but I was a little disappointed since it's the first thing I feel the need on xubuntu and I really liked the basic and intuitive gnumeric interface

---

### Post by kumoshk on 2012-04-10
Gnumeric is supposed to be better than other spreadsheets (even Microsoft Office, which is said to have some issues) with the accuracy and number of its formulas, but I agree that it really needs to have some import/export filters for xlsx, among other things. And OpenOffice needs to be able to 'open' Gnumeric files.

Of course, Microsoft needs filters for everything, too.

---

### Post by kumoshk on 2012-04-10
Gnumeric does export as xlsx now. Sorry, I didn't notice the save as option for Excel 2007. Try that.

---

### Post by Hagar Delest on 2012-04-11
Better avoid the OOXML format, have a look at: [MS Office 2007 OOXML file format (docx, xslx, pptx, ppsx)](http://user.services.openoffice.org/en/forum/viewtopic.php?f=5&t=4542).
Standards like ODF (native format for OOo) have been designed for interoperability. OOXML has not bee designed for that. MS will continue the vendor lock-in policy to keep their market shares...

If you need to open xlsx, then buy MS Office.

---

### Post by kumoshk on 2012-04-11
We should campaign for a Gnumeric revolution. (Meaning, encouraging businesses to use it.)

---

