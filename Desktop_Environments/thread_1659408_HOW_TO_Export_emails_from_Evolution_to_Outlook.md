---
title: "HOW TO: Export emails from Evolution to Outlook"
date: 2011-01-04
forum: Desktop Environments
---

### Post by Man with Hat on 2011-01-04
Hi, 

this thread may not be in the right area, so if it needs moving then please do that. After a VEERRRYY frustrating try to get my Evolution emails into Outlook, I can now say that the whole process is quite simple. It seems clunky the way that I have done it, but it is free and it works!

First download and this [[COLOR="Red"]Free Converter[/COLOR]]("http://www.outlookimport.com/downloads/mbox-eml-extractor.exe") to convert *.mbx into *.eml
If the link is broken, it came from [_http://www.outlookimport.com/_]("http://www.outlookimport.com/") and you just have to find their link to the mbx to eml converter.


***IN LINUX***
1) Open Evolution
2) Highlight the emails that you wish to convert, CTR+A for all in folder
3) R-click and "save as" and call the file anything you want with an mbx extension (example: inbox.mbx) - *note*: you may need to save this somewhere that Win/linux both recognise as Windows refuses to recognise drives formatted by linux. ie. save on a drive that has been formatted in FAT32 or NTFS

***IN WINDOWS***
1) Open mbox-eml-extractor.exe (the free converter, probably in your downloads directory)
2) Click "Add" and select your *.mbx file that you saved
3) Click "process" and select the output directory (I just created one on the desktop)
4) Open **Microsoft Outlook Express** NOT OUTLOOK!! It comes free with your windows install
5) Open the directory that you saved the *eml files (the "process" ones) and drag n drop into MS outlook express
6) All of your emails should show up in MS Outlook express now
7) Click File->Export->Messages
8) You will not be given an option where to save it but if you are curious, go to Tools->Options and click the Maintenance tab and the "Store folder" button to see the path
9) After it has exported now open **Microsoft Outlook** and click File->Import and Export and select "Import Internet mail and addresses" and press next. Choose "outlook express" etc and follow the bouncing ball so to speak.
10) VOILA!! You have managed the frustratingly and seemingly impossible. Now if Evolution soon gets an export to pst (or whatever the extension is) we won't need this thread anymore

Anyway I really hope this helps someone as it took me quite a while to find this solution. Any feedback welcome!!

---

### Post by frogotronic on 2011-06-16
Do you have to do each folder individually?

---

### Post by tommynz1975 on 2012-03-01
Well done you...  have systems to work on today..

if I do this per folder its no biggy its just life.

---

### Post by Man with Hat on 2012-06-21
Sorry for not replying earlier, didn't realise people actually read this! Glad it's helping!

As far as I can remember, you do have to do this for each folder as you have to ctl+A to select all emails visible. Believe me though, after the amount of headache from trying to do this, it is by far the quickest way I've ever found (well only way to be honest).

---

### Post by Franc Kaos on 2013-06-12
Just wanted to post my thanks, even years later it's posts like this that keep me on the Ubuntu path.

---

### Post by cincinnatus13 on 2013-06-12
I know this is old but couldn't you just use Thunderbird which saves the emails in .eml format already? Would save you the trouble of converting anyway.

---

### Post by Iowan on 2013-06-12
Closed - old thread.

---

