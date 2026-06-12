---
title: "[SOLVED] OpenOffice opens doc with wrong application - Word instead of Spreadsheet"
date: 2008-03-31
forum: Desktop Environments
---

### Post by MountainX on 2008-03-31
I have a tab delimited text document I opened once in OpenOffice Word Processor. (I may have saved it, but I didn't intend to do that.) Now, every time I right click the file and tell it to open with OpenOffice Spreadsheet, it opens instead with OpenOffice Word Processor. How do I resolve this? Thanks.

---

### Post by Bubba64 on 2008-03-31
You can probably re save it in a spread sheet format open it go to file save as and open the drop down and save as spread sheet. I don't know if this will work but you also may be able to paste into spread sheet.

---

### Post by Antispaceman on 2008-03-31
Right Click it
Properties
Open With tab
Add spreadsheet to that by clicking the add button
Then delete writer program from the menu

Or just right click and click open with for one time only opens

---

### Post by MountainX on 2008-03-31
> **Antispaceman said:**
> Right Click it
Properties
Open With tab
Add spreadsheet to that by clicking the add button
Then delete writer program from the menu

Or just right click and click open with for one time only opens

I have been doing all those things (except deleting the writer program from the context menu). However, it always opens with the wrong app.

I even opened the file in a text editor, and saved it with a new name and the same thing happened.

---

### Post by Jouke74 on 2008-03-31
I had the same problem and looked for about an hour to solve it. Luckily the FAQ of Openoffice (which of course you should read straight) helped:

[http://documentation.openoffice.org/faqs/spreadsheet/001.html](http://documentation.openoffice.org/faqs/spreadsheet/001.html)

0. Rename the file to .txt or .csv

1.  Open Calc. In the pull-down menus, go to File > Open.

2. Browse to find and select the ASCII file.

3. Select File type: Text CSV (.csv; .txt). Note: This choice is near the bottom in the spreadsheet file types section of the list.

4. Now click Open.

5. In the dialog that appears next, select the Separator options. These are the characters or methods used in the file to separate the fields of data. The same methods must be specified in this box as those used in the file to import the data into a spreadsheet. After selecting the separator type, a preview of the data will be displayed in the Fields section. If the data visually lines up in columns, then the correct separator has been selected. If not, a different separator type may be used in the file. The goal is to match the correct character used as a separator in the file, so that the data will line up nicely in the visible cells. When the data lines up, click OK.

Cheers, JJ.

---

### Post by MountainX on 2008-03-31
Thanks for the answer and the link. That works.

---

