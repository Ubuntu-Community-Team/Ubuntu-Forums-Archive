---
title: "file type unknown  (application/octet-stream) is not suppo"
date: 2009-03-03
forum: General Help
---

### Post by shateredsoul on 2009-03-03
I keep getting that message when I try to open a pdf from an article that was sent to me.  Any ideas on how to open this ?

it does not say, "could not find mime type".. most of the posts were about that instead.

---

### Post by john183 on 2009-03-03
Try saving the PDF to your HD first. It sounds like there is a disconnect between your web browser and the PDF software.

On another note, I am not sure that a PDF file should be being identified as an "application/octet-stream" mime type. That sounds more like a program, most likely a windows program.

---

### Post by shateredsoul on 2009-03-03
That's weird,.. what about the following message?

File type RAR archive (application/x-rar) is not supported?  I got that when I tried to view a comic using Comix.  It's a cbr file.

---

### Post by shateredsoul on 2009-03-03
I think this might be because I don't have an unrar program.. i'm going to install that and see if it fixes the issue

---

### Post by shateredsoul on 2009-03-03
nope any ideas? the cbz files work fine.. but cbr won't open with Comix

*edit* when I rename the file to .rar I cant open it and view the jpgs inside.  Is there a way to unrar.. the format to a .cbr file?

*edit again*  Actually if I rename it .rar I can look inside, but I can't unrar it nor can I extract it (or copy the files inside and paste in another spot)

Ideas? Anyone?

---

### Post by fragos on 2009-03-03
application/octet-stream is a catch all that correctly applies to any file. Mime type can be determined by examining the content or by implying from the file extension, e.g. .pdf. Some programs only use the extension to determine type. Try editing the file name to set the extension to PDF. On occasion PDF files downloaded from the web come with the wrong or no extension.

---

### Post by shateredsoul on 2009-03-03
Good suggestion, but it's not working.  To be clear.. it's a ".cbr" extension which is a rar type file.  It is often used to store comic books.  When I rename the file to ".rar" I can look inside and I can even see the thumbnails of the jpgs.  Unforunately I cannot open the actual file nor can I use comix to fiew the .cbr rar. I also cannot unrar the folder.

---

### Post by fragos on 2009-03-03
When you right click a file and select Properties you can then set the "Open with" parameters for whats the default ap and what others are avaible in the right click drop down menu. Do you have an ap registered for the CBR extension?

---

### Post by endotoxin on 2009-03-20
shateredsoul: I ran the following commands and now have .cbr support without any problems:

[B]sudo apt-get install rar
sudo apt-get install unrar[/B]

===

Also, I made sure that I got the latest build from SF, v4.0.3, instead of the build available from the ubuntu repositories, which was only a version 2.something.

---

### Post by ubeautu on 2010-03-08
> **endotoxin said:**
> 
[B]sudo apt-get install rar
sudo apt-get install unrar[/B]

.

Thanks : this is the fix that I needed too. Seems like my comic readers were installed and running happily but had no way of rar/unraring! :popcorn:

---

### Post by Kanemba on 2011-05-17
Hi all, I need your support, I have just moved to ubuntu and I have a very important report which I cannot retrieve. I get the following msg when I open it File type unknown (application/octet-stream) is not supported  when I  click direct BUT when I right click, it says recovery failed and take me to ASCII FILTER.
Can you help , I am very desparate indeed.
Boniface

---

### Post by doas777 on 2011-05-17
mime types just tell your Browser how to open a given file type, so if you save the file to your desktop first, and then attempt to open it, everything should work fine as long as you have the right application to open it with, and the file is undamaged. 

what type of file is your report?

and in future, start your own thread instead of jumping on one that is more than a year old. 
when the mods see this, they will likely assume that you are up to no good.

---

### Post by fonsi2099 on 2011-07-14
The same problem for me, 
Hi all, I need your support, I have updated from 10.10 to 11.04 ubuntu and I have my office docs, (Open Office,today Libre Office) which I cannot retrieve. I get the following msg when I open the PDF docs- "Files type unknown (application/octet-stream) is not supported" and for office docs I get, when I click direct BUT when I right click, it says recovery failed and take me to ASCII FILTER and after opening I get not text. 

Thanks for any help
:confused:

---

### Post by anandrohit_29 on 2011-09-08
**file type unknown  (application/octet-stream) is not supported**             
                                                                I keep getting that message when I try to open a pdf from a file that was sent to me.  Any ideas on how to open this ?

And when i'm copy-past on my map drive at window server 2008 r2 so, i'm getting this kind of error or its not saving the file on windows server...please if anyone know about this problem...so please reply......

---

### Post by fragos on 2011-09-08
Some applications examine file contents to determine file type but others still depend on the file extension, e.g. .pdf. On occasion I've downloaded what claimed to be PDF but were actually HTML. If the file dosen't have a .pdf extension try editing the file name. You could also examine the file with Hex editor or Gedit. It may not be what it claims to be.

---

