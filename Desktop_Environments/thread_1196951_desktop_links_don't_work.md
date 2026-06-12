---
title: "desktop links don't work"
date: 2009-06-25
forum: Desktop Environments
---

### Post by revtds on 2009-06-25
After working with a Java Runtime macro to try and convert gnucash xml files to QIF files for quicken 2001, I discovered this morning that all of my Firefox links to the many websites on my desktop all open in OpenOffice spreadsheet or word processor, instead of a Firefox browser page.


I am not sure where to even begin with this, as I have looked the Prefs for Firefox and Openoffice and found nothing helpful, as well as the properties for the links.  The only anomaly I see is that they all say that the permissions cannot be determined on each link.    ????????

Athlon 1G, 2G RAM, ATI onboard video, Ubuntu Hardy Heron with latest stable kernel, system fully updated daily.

---

### Post by days_of_ruin on 2009-06-25
Did you look at the Properties>Open With tab?

---

### Post by revtds on 2009-06-25
There is no "open with" tab in the properties box, nor is there an "open with" option on the dialog box if you right click.  That was the first thing I looked for.

---

### Post by VCoolio on 2009-06-25
You can set user preferences for preferred applications for any filetype in 
~/.local/share/applications/mimeapps.list

---

### Post by days_of_ruin on 2009-06-25
```
gconftool-2 --get /desktop/gnome/applications/browser/exec
```

What is the ouput of that command?

---

### Post by revtds on 2009-06-28
As a response to PY, the output of the command is "Firefox"

In response to vcoolio, I have pasted a previous copy of "mimeapps.list" and the current one.  If I make the old copy a current copy, then my desktop icons begin to operate as anticipated.  My question is, if you have an idea, what changed the file, and why?

Current mimeapps.list:

[Added Associations]
application/x-extension-WAB=gedit.desktop;
audio/x-ms-asx=firefox.desktop;totem-gstreamer.desktop;

******
Previous copy:

[Added Associations]
application/x-extension-WAB=gedit.desktop;
audio/x-ms-asx=firefox.desktop;totem-gstreamer.desktop;
image/jpeg=ooo-draw.desktop;
application/zip=ooo-writer.desktop;
application/pdf=evince.desktop;xpdf.desktop;ooo-writer.desktop;
application/xml=ooo-calc.desktop;
application/msword=ooo-draw.desktop;
text/html=ooo-calc.desktop;

---

