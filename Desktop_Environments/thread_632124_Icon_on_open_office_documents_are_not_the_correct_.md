---
title: "Icon on open office documents are not the correct one"
date: 2007-12-05
forum: Desktop Environments
---

### Post by pdeville on 2007-12-05
I just installed Lotus notes 8 on ubuntu 7.10. Unfortunatley Notes replaced the default action on openoffice documents. I changed the mime info in  /usr/share/mime/... and rebuild the mime database in order to have openoffice application associated to open offce document.** But The icon on the document are still the lotus notes one and I don't know how to change that.**

---

### Post by petsimbe on 2008-02-06
I had same problem after installing IBM Lotus Symphony. IBM Lotus Symphony rewrote all Open Office document icons.

I found that in icons directories are open document icons linked to the "IBM Lotus Symphony icons" and not to the "Open Office document icons".

This link has to be changed or be replaced by "Open Office document icons". MIME  I did not  change 

For example in my case>

the MIME name for the *.ODT file (open office word file) is [COLOR="Navy"]application-vnd.oasis.opendocument.text[/COLOR]
and name of the open Office Writer documents icon is [COLOR="Navy"]openofficeorg23-oasis-text.png[/COLOR]

So I replaced the link in terminal under root privilege (sudo) in directory

[COLOR="Navy"]cd usr/share/icons/hicolor/48x48/mimetypes/
sudo rm application-vnd.oasis.opendocument.text.png
sudo cp openofficeorg23-oasis-text.png application-vnd.oasis.opendocument.text.png
[/COLOR]
(note that in my case [COLOR="Navy"]./hicolor[/COLOR] is directory with used theme and[COLOR="Navy"] ./48x48 [/COLOR]is directory with icons in certain resolution )

All of that I repeated for all the directories involved ( resolutions as 16x16, 32x32 … ) and for all the open office file types. I used script do do it.

Open office document icons launched after session restart.

see [http://www.linuxcommand.org/](http://www.linuxcommand.org/)
see  [http://ubuntuforums.org/showthread.php?t=150393&highlight=change+icon](http://ubuntuforums.org/showthread.php?t=150393&highlight=change+icon) 
__________________
Forward Message

---

### Post by Macros42 on 2008-02-12
This is odd. If I "locate ooffice-oasis" It finds the pngs in the 48x48/mimetypes directory. This is after an updatedb. But ...

:~/.local/share/icons/hicolor/48x48/mimetypes$ sudo cp ooffice-oasis-spreadsheet.png  application-vnd.oasis.opendocument.spreadsheet.png
cp: cannot stat `ooffice-oasis-spreadsheet.png': No such file or directory

Any ideas?

[edit]Scratch that - I was in ~/.local... Doh!

---

### Post by urgnom on 2008-03-14
So I replaced the link in terminal under root privilege (sudo) in directory

[COLOR="Navy"]cd usr/share/icons/hicolor/48x48/mimetypes/
sudo rm application-vnd.oasis.opendocument.text.png
sudo cp openofficeorg23-oasis-text.png application-vnd.oasis.opendocument.text.png
[/COLOR]
(note that in my case [COLOR="Navy"]./hicolor[/COLOR] is directory with used theme and[COLOR="Navy"] ./48x48 [/COLOR]is directory with icons in certain resolution )

Thanks, you solved my problem! :guitar:

---

