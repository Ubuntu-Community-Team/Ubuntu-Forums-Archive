---
title: "OpenOffice needs 10 full minutes to start"
date: 2005-01-05
forum: Desktop Environments
---

### Post by Bart Van on 2005-01-05
When starting the OpenOffice writer, it takes 10 full minutes to start!!
The splash screen comes up, the little blue bar moves nicely until the end and then nothing else happens - until 10 minutes later when I finally get my new document and can start typing!

Help!

I also installed AbiWord which is very speedy, but which doesn't read my .sxw files :(

---

### Post by hardcandy on 2005-01-05
How much RAM do you have on your computer? Open Office Writer, go to options, then to Memory, and increase the amount of RAM OO can use. I think the default is 9 MB, I increased mine to 32 MB.

---

### Post by burlap on 2005-01-05
Memory settings in the OpenOffice preferences have different purpose - it is memory dedicated to graphics. OpenOffice itself uses hundreds of MB, so neither 9 or 32 are enough anyway. 

I had this problem with OO and the solution was to get rid of ~/.openoffice/user/psprint/pspfontcache file (or create one with different permissions to prevent OO from writing there). However, I do not have any problems with Ubuntu OO so far (pspfontcache is still 32 kB) - check your pspfontcache, if it seems too big, delete it (backup just in case) and start OO.

---

### Post by Bart Van on 2005-01-05
[QUOTE=hardcandy]How much RAM do you have on your computer? Open Office Writer, go to options, then to Memory, and increase the amount of RAM OO can use. I think the default is 9 MB, I increased mine to 32 MB.[/QUOTE]

256 MB RAM on a 1800 Mhz AMD processor, should be enough... On my previous Mandrake 10.0 system (on the same machine) OpenOffice worked perfectly - it always seems a bit slow to start, I have no problems with that, but 10 minutes is slightly exaggerated...

Changing the memory setting doesn't help, I already tried that - but thanks for replying anyway!

---

### Post by Bart Van on 2005-01-05
Thanks for the tip, I'll try when I get home and post the results here...

---

### Post by hardcandy on 2005-01-05
Another tip I found was to download and use "ooqstart". I'm not at the Ubuntu machine now so I do not know if it is in the Ubuntu repositories. 
[http://packages.debian.org/testing/x11/ooqstart-gnome](http://packages.debian.org/testing/x11/ooqstart-gnome)

It creates an applet that you put on the taskbar and it preloads OO. It takes about 22 MB RAM while it sits there according to the docs. 

"If you are using a version of GNOME that includes both gnome-core and gnome-core-devel, get ooqstart, install it, and put the applet on your panel to drastically cut down on OpenOffice.org's startup time."

---

### Post by Darrena on 2005-01-05
[QUOTE=Bart Van]When starting the OpenOffice writer, it takes 10 full minutes to start!!
The splash screen comes up, the little blue bar moves nicely until the end and then nothing else happens - until 10 minutes later when I finally get my new document and can start typing!

Help!

I also installed AbiWord which is very speedy, but which doesn't read my .sxw files :([/QUOTE]
 If you start OO writer from the console does it give you any errors while loading?

---

### Post by Bart Van on 2005-01-05
[QUOTE=Darrena]If you start OO writer from the console does it give you any errors while loading?[/QUOTE]

No, just sits there if I recall correctly (I'm not at my Ubuntu-machine right now...)

One strange thing though, is that when I start OpenOffice "empty" (with the command ooffice - or is it soffice?), it pops up almost immediately - but without document of course. In that case, the ten minutes start counting when I choose "new text document"...

---

### Post by Bart Van on 2005-01-05
[QUOTE=burlap]Memory settings in the OpenOffice preferences have different purpose - it is memory dedicated to graphics. OpenOffice itself uses hundreds of MB, so neither 9 or 32 are enough anyway. 

I had this problem with OO and the solution was to get rid of ~/.openoffice/user/psprint/pspfontcache file (or create one with different permissions to prevent OO from writing there). However, I do not have any problems with Ubuntu OO so far (pspfontcache is still 32 kB) - check your pspfontcache, if it seems too big, delete it (backup just in case) and start OO.[/QUOTE]It's only 20.7 Kb, but changing the permissions to read-only didn't help...

---

### Post by Bart Van on 2005-01-05
[QUOTE=hardcandy]Another tip I found was to download and use "ooqstart". I'm not at the Ubuntu machine now so I do not know if it is in the Ubuntu repositories. 
[http://packages.debian.org/testing/x11/ooqstart-gnome](http://packages.debian.org/testing/x11/ooqstart-gnome)

It creates an applet that you put on the taskbar and it preloads OO. It takes about 22 MB RAM while it sits there according to the docs. 

"If you are using a version of GNOME that includes both gnome-core and gnome-core-devel, get ooqstart, install it, and put the applet on your panel to drastically cut down on OpenOffice.org's startup time."[/QUOTE]Thanks for the tip, but I only want it to start at the "normal" speed instead of after 10 minutes. I think I have a problem somewhere I should solve first (getting down the 10 minutes to let's say 30 seconds), and then think about ooqstart...

---

### Post by hardcandy on 2005-01-05
You know, I just realized, it was never said if you had the jre installed or not. I'm wondering if that would speed things up. I think Ubuntu may have blackdown java installed and I'm wondering if the Sun version of java might not be a little faster.  I installed it and the Mozilla plugin 10 minutes after I had installed Ubuntu and did not think to even ask that question.
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by jdodson on 2005-01-05
[QUOTE=hardcandy]You know, I just realized, it was never said if you had the jre installed or not. I'm wondering if that would speed things up. I think Ubuntu may have blackdown java installed and I'm wondering if the Sun version of java might not be a little faster.  I installed it and the Mozilla plugin 10 minutes after I had installed Ubuntu and did not think to even ask that question.
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)[/QUOTE]

installing java or blackdown would not make openoffice any faster.  openoffice uses java for ODBC database functionality(MySQL, PostgreSQL, etc) and the like.

---

### Post by jdodson on 2005-01-05
[QUOTE=Bart Van]When starting the OpenOffice writer, it takes 10 full minutes to start!!
The splash screen comes up, the little blue bar moves nicely until the end and then nothing else happens - until 10 minutes later when I finally get my new document and can start typing!

Help!

I also installed AbiWord which is very speedy, but which doesn't read my .sxw files :([/QUOTE]

i downloaded a version of abiword that did read openoffice .sxw files, however that was a few years ago.  the formatting support was pretty bad, but you could at least get the text in and reformat it.  i wonder why they removed the functionality?

**EDIT** looks like it is available as a plugin now:

[http://www.abisource.com/twiki/bin/view/Abiword/PluginMatrix#Import_Export_Filters](http://www.abisource.com/twiki/bin/view/Abiword/PluginMatrix#Import_Export_Filters)

---

### Post by CowPie on 2005-01-05
[QUOTE=Bart Van]When starting the OpenOffice writer, it takes 10 full minutes to start!!
The splash screen comes up, the little blue bar moves nicely until the end and then nothing else happens - until 10 minutes later when I finally get my new document and can start typing!

Help!

I also installed AbiWord which is very speedy, but which doesn't read my .sxw files :([/QUOTE]
 I would install abiword and the following (listed as "suggested" in dpkg):

ii  abiword        2.2.1-1-warty+ WYSIWYG word processor based on GTK2
ii  abiword-common 2.2.1-1-warty+ WYSIWYG word processor based on GTK2
ii  abiword-doc    2.2.1-1-warty+ Documentation for AbiWord
ii  abiword-plugin 2.2.1-1-warty+ Plugins for AbiWord
ii  abiword-plugin 2.2.1-1-warty+ Plugins for AbiWord (with GNOME dependency)

---

### Post by Bart Van on 2005-01-07
I tracked down the problem to my ADSL-connection... When I'm not connected, OpenOffice starts almost immediately; when I'm connected, it takes 10 minutes  :confused: 

Even better, while waiting for OO to appear (during connection), stopping my connection makes it appear instantaneously...

I use the eagle-usb-2.0.0 driver, I'll head over to their forum and see if they can help.

Thanks for your help everyone!

---

### Post by Bart Van on 2005-01-08
[QUOTE=Bart Van]When starting the OpenOffice writer, it takes 10 full minutes to start!!
The splash screen comes up, the little blue bar moves nicely until the end and then nothing else happens - until 10 minutes later when I finally get my new document and can start typing!

Help!

I also installed AbiWord which is very speedy, but which doesn't read my .sxw files :([/QUOTE]

Finally I solved the problem, it was related to CUPS. 
As I am not on a network, I disabled the /etc/init.d/networking service at startup - but this also disabled CUPS. (When I tried to start the Printing Manager in the System Configuration menu, I got the error "unable to reach CUPS server", and [http://localhost:631](http://localhost:631) didn't work either...) Didn't notice this before as I have no printer attached...

Apparently OpenOffice tries to reach the CUPS server as well on startup and didn't succeed in my case, hence the long wait...

So I returned /etc/init.d/networking to it's original state, did ```
/etc/init.d/networking start
```, and thus solved all the problems with CUPS and OpenOffice...

Yihoo!  :D

---

