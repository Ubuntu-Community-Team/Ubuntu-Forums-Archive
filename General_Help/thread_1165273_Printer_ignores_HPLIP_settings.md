---
title: "Printer ignores HPLIP settings"
date: 2009-05-20
forum: General Help
---

### Post by Tootler on 2009-05-20
I have a HP PSC 1510 printer which works fine in Ubuntu for basic printing tasks, but if you want to do anything more sophisticated, then there are problems.

I produce a newsletter for a couple of organisations on a regular basis. I produce these using Open Office and print them out in booklet format (Two A5 pages per side of A4). In the past, I have produced the booklet on A4 Pages and then sent them to the printer and by selecting the appropriate printer options, the printer software will sort everything out, printing the A4 pages as two A5 pages on a single A4 sheet, double sided with the page order all sorted out. In Ubuntu, the options in the print dialog box are fairly limited, although you can set the booklet format up using the OO print options, you still have to make sure you print in the correct order so that the booklet will come out correctly, whereas previously this was all sorted out.

The second problem concerns printing a pdf document. I had a document in OO on an A5 page. As I had to send it to someone, I turned it into a pdf and before sending it, tried printing the document from the document viewer. I loaded the printer with A5 paper and selected print only for the printer to take in the paper and the fault light on the printer started flashing and an error message came up. On checking the HPLIP log, the error message was "Media Mismatch". I tried again, this time with A4 paper and the document printed fine, even though it was originally an A5 document. So I tried again with A5 paper and this time checked the Print dialog box. The available settings were very limited and several of these were greyed out. Conspicuous by its absence was any means of setting the paper size, which seems a serious omission in the first place.

I have checked the HPLIP toolbox on a couple of occasions and all the settings I need - and more - are available in the Print Settings Tab, but when I have tried changing the settings, they are ignored by the printer which only seems to respond to settings in the Print dialog in the application you are printing from. 

It seems odd to me that the HPLIP print settings are not available from the print dialog box in the various applications. It is frustrating that settings I want are there, but I do not seem to be able to use them.

Any suggestions?

Geoff

I am using Ubuntu 8.10

---

### Post by bryanl on 2009-05-20
The printer systems Linux systems still make me long for the OS/2 days ... 

As for printing brochures, that is usually easiest when done directly from OOo. Set the page to the double size and landscape then choose brochure from the print options. You can choose left then right to print both sides if you want.

---

### Post by Tootler on 2009-05-21
> **bryanl said:**
> The printer systems Linux systems still make me long for the OS/2 days ... 

As for printing brochures, that is usually easiest when done directly from OOo. Set the page to the double size and landscape then choose brochure from the print options. You can choose left then right to print both sides if you want.

That is, in fact, what I did. You don't need to set the page to double size or landscape. I simply produce the brochure on A4 in portrait then select brochure and OOo will sort it out and print two A5 pages side by side on A4 landscape. When selecting left then right, you need to remember that one has to go through in reverse order and the other forward. That is the advantage of doing it through the printer settings, that is sorted as well. 

Also this does not sort the other issue of scaling the pdf. and one of the features of pdf is that it is scaleable. I take advantage of this for posters. You can print a few A4 size for the notice board then print a bunch on A5 for handbills without having to produce two documents.

It seems to me that the Linux printing set up is several years behind the times. They do not seem to have caught up with the capabilities of modern printers and the software that accompanies them. My PSC 1500 is by no means a high end printer yet is capable of printing in a range of formats from a basic document. Even nine years ago I could produce a banner for my Dad's 80th birthday on fanfold paper from a basic document set up on A4 sheets using an earlier model HP printer. 

Geoff

---

### Post by Tootler on 2009-05-21
Solved the printing of A5 pdf files.

Adobe produce a Linux version of the Acrobat Reader and it is available in the repository. You can install from the Packet manager, or 

```
sudo apt-get acroread
```

from the terminal.

You will have to accept a license agreement on startup.

This doesn't really solve the original issue, though. How can you get printout to recognise print settings from the HPLIP toolbox?

---

