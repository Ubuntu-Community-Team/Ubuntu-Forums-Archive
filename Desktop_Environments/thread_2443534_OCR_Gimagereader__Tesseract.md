---
title: "OCR Gimagereader / Tesseract"
date: 2020-05-16
forum: Desktop Environments
---

### Post by Alistair George on 2020-05-16
This is not a question, rather help for those who are trying to export OCR text file with correct formatting.
Forget the setting information from others about using a file config.txt in same directory as (PDF) source; (preserve_interword_spaces 1) does not appear to work even on later versions of Tesseract so here is how to get formatting you require.
Typically, I was using pdf bank statements which had good spacing between columns but the reader despite config setting only put inserted 1 space, and the data was not as accurate as the method described below.

You need to massage your data in 2 steps:
1..open the pdf in GimageReader and for each column you want, with setting TEXT select the items in that column only, scan, and repeat process until you have a single column of all the data from your pdf in text file which you import to openoffice.calc
note that you must keep each item as a single line you can see where Ive commented I would remove (empty line) and in the payees there is a several line item; you need to remove the other lines from multiline items.
[ATTACH=CONFIG]285898[/ATTACH]
2..paste the data in to calc. Say first column date, you leave that data in place, select all the next column data, cut and then paste into next column and so on.

The above method works a treat and within GimageReader you can manually scan several pages and using the text edit mode, massage your data into whatever layout you want just ensure to keep in single column.

Hope this helps someone as I was stymied for a day before figuring this out.
Al.

---

