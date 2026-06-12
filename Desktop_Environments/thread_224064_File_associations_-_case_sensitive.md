---
title: "File associations - case sensitive?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by peterwr on 2006-07-27
*** RESOLVED *** - see #6 and #7 below. 

I've changed my file association for pdf documents to Adobe Reader. When I open a file with a .PDF extension it works fine, but when I try to open a file with a .pdf extension, I get the following error message:

[INDENT]The filename "TUX_Issue15_July2006.pdf" indicates that this file is of type "pdf document". The contents of the file indicate that the file is of type "PDF document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "PDF document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. [/INDENT]

Any ideas? Presaumably the file type is case-sensitive, but how do I make it non-case-sensitive? I can see this will be a problem for other file types too.

TIA,

Peter

---

### Post by jd65pl on 2006-07-27
I know unix is specific on its use of case. File extentions should be in lower case in most systems.

---

### Post by peterwr on 2006-07-28
Hi Jamie

Thanks for replying. Yep, it's the case sensitive bit that seems to be the problem. If I click on a file with a .PDF extension, it opens in Reader without a hitch. If the file has a .pdf extension, though, I get the error message. If I right-click the file and select Open with > "Adobe Reader" it also opens without a fuss. It seems to be whatever mechaninism kicks in when I double-click the icon that's causing the problem; I was wondering if there's any way to change/edit that. 

More info: if I change the filename so it has a .PDF extension, it opens with a double-click, and thereafter, "Open with Adobe Reader" shows up as the top item in the right-click menu, even if I rename it back to .pdf - but only for a file I've renamed. If  I then right-click on a file that hasn't been renamed, "Open with Adobe Reader" shows up briefly, then disappears. 

Not a show-stopper, but I'd really like to know wht the heck's going on. Anybody?

Cheers,


Peter

---

### Post by parktownprawn on 2006-09-20
my crude solution is posted on

[http://www.ubuntuforums.org/showpost.php?p=1521481&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1521481&postcount=5)

---

### Post by loucomballa on 2007-05-25
I've got the same problem with pdf files. At some point gnome stoped openning pdf files by double clicking on them. I complained that filenam (pdf) did not match content (PDF) and the file might be threat to the system. However, by 'Opening with..evince' the program opens the file with no problem.

Apparently there must be some cases sensistive problem with mime types and gnome.

Any ideas?

---

### Post by loucomballa on 2007-05-25
OK, I've solved the problem :
First I've removed the file
```
.local/application/evince-usercustom.desktop
```
and then removed in the file
```
.local/applications/mimeinfo.cache
```
the line pointing to evince-usercustom.desktop for mimetypes application/pdf.
However I'm still wondering how I ended up with such configuration (new user in the same system did not face the problem, and two weeks before neither me)
Cheers,

Xavi.

---

### Post by peterwr on 2007-07-27
YESSSSS!!!

Thanks, Xavi. That fixed it. I looked in ~/.local/share/applications/ and found desktop config files for Acrobat Reader, Adobe Reader and Evince. I created a folder called "disabled" and moved the config file there. Problem solved. By moving each of them in turn back to the applications folder, I narrowed the problem down to the Adobe Reader desktop config file. Leaving it in disabled solves the problem completely, whichever app is nominated as the default. 

I've not needed to tinker with mimeinfo.cache so far. 

Many thanks for the pointer.

---

