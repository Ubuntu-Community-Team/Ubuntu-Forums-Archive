---
title: "launcher: start .ods file"
date: 2009-06-05
forum: General Help
---

### Post by equiplist on 2009-06-05
Hello All, 

I recently switched from Windows Vista to Linux Ubuntu 9.04.  I started out w/ DOS in the early 80's, and stuck with Microsoft all this time.  Frustrated w/ Windows in recent times, I had considered Apple/Mac a while back, but stood pat.  Just didn't see the value in the added expense for the hardware.  Am glad I made the change to Linux.  Went through some difficulty at first, but am now well adjusted to the new OS.  

Question: I want to set up a launcher in my Main Menu, to start an OpenOffice spreadsheet .ods file.  Just entering the file name as a command does not work.  I couldn't find a quick answer to this, so I thought to write here.  Replies are very much appreciated.  

All the best, Barry, equiplist
Equipment Recyclers, 443-850-8494, call anytime
[http://stores.shop.ebay.com/Equipment-Recyclers](http://stores.shop.ebay.com/Equipment-Recyclers)

---

### Post by michy99 on 2009-06-05
Try this:```
ooffice -calc filename
```Replace 'filename' with the name of the spreadsheet.

---

### Post by equiplist on 2009-06-06
Perfect!  Thanks, very much.  Barry

---

### Post by colau on 2009-06-06
> **michy99 said:**
> Try this:```
ooffice -calc filename
```Replace 'filename' with the name of the spreadsheet.
Sorry for this post.
Would you please tell what does this command do?

---

### Post by Chronon on 2009-06-07
It opens "filename" in OpenOffice Calc (the spreadsheet program).

Did you read the original post?

---

### Post by ad_267 on 2009-06-07
You can change the launcher type to a location instead of a command. Then you can pick the file from a file chooser dialog and it will automatically choose which application to use to open the file.

---

### Post by Chronon on 2009-06-07
Nice tip, ad_267.  Thanks!

---

### Post by mrsray on 2010-04-03
THANKS from me too, been trying to do this for a while now  :roll:

> **michy99 said:**
> Try this:```
ooffice -calc filename
```Replace 'filename' with the name of the spreadsheet.

---

