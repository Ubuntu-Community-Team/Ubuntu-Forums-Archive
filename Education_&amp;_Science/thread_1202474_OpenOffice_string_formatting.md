---
title: "OpenOffice string formatting"
date: 2009-07-02
forum: Education &amp; Science
---

### Post by tpmoney on 2009-07-02
Ok, so I've been beating my head against the wall trying to get this one sorted out. I have a spreadsheet in open office, I have a bunch of fields that are all 12 character alphanumeric strings. I want these fields to display with MAC address formatting something like: 12:34:46:78:AB:CD.

If I go into Format -> Cells, I could do this if the field were just full of numbers (with format string ##:##:##:##:##:##) but that doesn't work on text fields.

Looking around I've found that these formatting strings can be separated into sections with semicolons to get different formatting depending on the field content. Officially OO's documentation says these fields are:

positive;negative;zero

Investigating further suggests that excel allows one step further of:

positive;negative;zero;text

So I tried giving it the format string of:

;;;##:##:##:##:##:##

which does format the cell, but instead of giving me my field formatted as a MAC address, I quite literally get the string:

##:##:##:##:##:##

And I can't seem to find what open office might take for a wild card so that I can get my cell formatted. Any ideas? I'm really hoping I'm just missing something obvious and that this is indeed possible.

---

### Post by aaronrus on 2012-11-26
[http://www.winko-erades.nl/index.php?option=com_content&view=article&id=22:convert-mac-address-in-ms-excel-or-oo-spreadsheet&catid=10&Itemid=5](http://www.winko-erades.nl/index.php?option=com_content&view=article&id=22:convert-mac-address-in-ms-excel-or-oo-spreadsheet&catid=10&Itemid=5)

---

### Post by cariboo on 2012-11-27
A three year old thread is still three years old. Closed.

---

