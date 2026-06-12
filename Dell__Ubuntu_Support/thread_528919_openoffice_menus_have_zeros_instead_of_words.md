---
title: "openoffice menus have zeros instead of words"
date: 2007-08-18
forum: Dell  Ubuntu Support
---

### Post by mmcfly8888 on 2007-08-18
Hello,

Every character in my menus in openoffice are zero's instead of words.  i have a brand new install of ubuntu 7.04.  i think it is a java problem because i was on a java applet online and all the characters were zeros as well.  i reinstalled everything in synaptic that had the word 'java' in it.  i have a ttached a screenshot.  if anyone can help me, thank you!!!

mmcfly8888

---

### Post by angryfirelord on 2007-08-18
Not a java issue, but a font issue. Try issuing:
```
sudo apt-get install msttcorefonts
```
I have no idea if this will work, but it may reload your fonts and fix the problem.

---

### Post by mmcfly8888 on 2007-08-18
no dice, but thanks... i tried removing it and reinstalling it... anyone else have any ideas???

---

### Post by Hagar Delest on 2007-08-20
See this thread (2 fixes) : [ Open Office Language]("http://ubuntuforums.org/showthread.php?t=529497").

---

### Post by jb201116 on 2007-09-11
> **mmcfly8888 said:**
> Hello,

Every character in my menus in openoffice are zero's instead of words.  i have a brand new install of ubuntu 7.04.  i think it is a java problem because i was on a java applet online and all the characters were zeros as well.  i reinstalled everything in synaptic that had the word 'java' in it.  i have a ttached a screenshot.  if anyone can help me, thank you!!!

mmcfly8888

Hi MMcFly8888,

Classic symptoms on open office I'm afraid..

Let me guess you are using either Mozilla, Firefox or SeaMonkey as your web browser... That behaviour is due to a MIME type being corrupted.

what you will need to do is open your browser and follow the below to rectify the issue..

(forgive me this is long)

DOCUMENT FILE TYPES							EXTENSIONS
-----------------------------------------------------------------------------------
application/msword 							doc wiz rtf                  
application/vnd.oasis.opendocument.text 				odt    
application/vnd.oasis.opendocument.text-master 			odm
application/vnd.oasis.opendocument.text-template 		ott
application/vnd.oasis.opendocument.text-web 			oth
application/vnd.stardivision.writer 				sdw vor     
application/vnd.stardivision.writer-global 			sgl
application/vnd.sun.xml.writer 					sxw              
application/vnd.sun.xml.writer.global 				sxg
application/vnd.sun.xml.writer.template 				stw

SPREADSHEET FILE TYPES AND THEIR 					EXTENSIONS
-----------------------------------------------------------------------------------
application/vnd.ms-excel 				    xls xlt xlm xld xla xlc xlw xll 
application/vnd.oasis.opendocument.spreadsheet 			ods 
application/vnd.oasis.opendocument.spreadsheet-template 	ots
application/vnd.stardivision.calc 					sdc           
application/vnd.sun.xml.calc 					 	sxc                
application/vnd.sun.xml.calc.template 				stc

PRESENTATION FILE TYPES AND THEIR 					EXTENSIONS
-----------------------------------------------------------------------------------
application/vnd.ms-powerpoint 					ppt               
application/vnd.stardivision.impress 				sdd sdp    
application/vnd.oasis.opendocument.presentation 		odp 
application/vnd.oasis.opendocument.presentation-template   otp
application/vnd.sun.xml.impress 					sxi            
application/vnd.sun.xml.impress.template 				sti

To modify one existent or to create a new one click on EDIT or NEW TYPE and enter the information needed, click on OK to save changes when finished. If Mozilla is not saving changes when creating or modifying mime types then you have a problem with Mozilla.

It's possible to delete any .mime.types or .mailcap (mind the "." in front of the names) in your home folder and restart your email client but some users can delete files they should not and deleted files are not recoverable.

Hope this helps..

jb201116

---

