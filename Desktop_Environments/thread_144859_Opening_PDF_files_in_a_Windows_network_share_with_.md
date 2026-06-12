---
title: "Opening PDF files in a Windows network share with Acroread"
date: 2006-03-15
forum: Desktop Environments
---

### Post by dadioflex on 2006-03-15
Hi! 

We scan paperwork here to pdf files on a shared folder on our Windows 2000 server. On a 766Mhz PIII running Breezy I was finding it pretty slow to use the standard Document Viewer to open these up for review so I installed acroread (learning in the process how to install ntlmaps so I could use the extra repositories through our isa firewal.)

Evil though it may be acroread is just *better* for viewing PDFs but while it works fine on local files I can't seem to get it to open any of the pdfs on the windows share. I did the connect to server to put the windows folder I need on my desktop. If I run acroread first and open file from the menu it doesn't show up the windows share I've mounted on my desktop so I can't even open that up and pick what I'm after.

I copied some pdfs to my local desktop, right clicked to properties and selected open with Adobe Reader by default but it still defaults to document viewer if I double click the file. Right click and select Open with Adobe Reader and it'll load the local pdfs fine. Neither double clicking or rightclicking and selecting open with application - Adobe Reader will open a pdf on the Windows share.

Alternatively is there any way to speed up the document viewer (Evince? Just the default Gnome document viewer) or get it to pre-load more of the pdf. At the minute it will only load 2 pages at a time and fairly slowly. I figured it might be a memory management thing but couldn't see anything obvious to change.



Also, if I copy from one folder on the Windows share to another am I at risk of FUBARing the NTFS file structure or will it be fine since I assume it's just me sending instructions to the W2000 server to make the changes.

Sorry about the ramble and about my general ignorance level - hopefully I'm using the right terms and not confusing matters further. Looking forward to any help you can offer me.

---

### Post by kaamos on 2006-03-15
You can mount the network shares. Then they will appear just as normal folders and all programs can access the files.

[http://ubuntuguide.org/#mountunmountnetworkfolders](http://ubuntuguide.org/#mountunmountnetworkfolders)

---

