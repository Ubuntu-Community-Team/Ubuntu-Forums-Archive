---
title: "can't get my printer to work, &amp; won't play disk"
date: 2009-03-27
forum: General Help
---

### Post by mikebarnett on 2009-03-27
I just got this and right now not too happy with it. I can't read any program I put in disk drive. It won't read my printer.
It tells me not connected yet when I use another op it reads it fine. It will reconize my printer but won't let it print.

---

### Post by Screwdriver0815 on 2009-03-27
for the printer (which model is it??) you should check if the device URI is correct. 

For that switch the printer on and open the browser (Firefox) and type into the adress line [http://localhost:631](http://localhost:631) 

this opens the printer configuration site of Cups (its inside the system, not in the internet) 

then you go to "manage printers" (or something similar, I don't know how it is written, as I have the german language) 
then you look at the printer model and the printer URI. It should be similar to 

usb://Brother/DCP-115C

but maybe it differs as you surely have a different printer. But at least it should display the Manufacturer and the actual model. If there is something strange (different model or so), click on "change printer" or something (again, I have the german langauge, so it could be slightly different from what I write), check the first dialog, click on "continue" and change the URI. Save the changes. You will prompted for your username and password, type it in and you are done.

you also could open a Terminal and type in:

lsusb

(assuming you have a USB-printer) when it is switched on.

Copy-paste the output in here and maybe someone can help you based on this.

Regarding the other issue:

which cd's do you want to be played? Is it music, or windows-programms? For sure, the windows-programms don't work of course. 
Music should be played. If not, some codecs may be missing.

---

