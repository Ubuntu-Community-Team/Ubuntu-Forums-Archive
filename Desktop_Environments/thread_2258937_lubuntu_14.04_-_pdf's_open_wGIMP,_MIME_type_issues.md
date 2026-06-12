---
title: "lubuntu 14.04 - pdf's open w/GIMP, MIME type issues"
date: 2014-12-31
forum: Desktop Environments
---

### Post by kenneth_myers2 on 2014-12-31
I'm frustrated with trying to figure this out.

I saved some web pages as PDF files on my desktop (from FF). When I double-clicked on one of them, they opened with GIMP instead of evince. I have tried MANY "solutions" to this problem after searching the web (I can't remember everything I tried, but it was alot), with no success. From what I can remember doing, I edited numerous files in directories such as /.local/share/applications (such as: defaults.list) and /usr/share/applications (such as: evince.desktop), tried to update global MIME type associations, used the GUI tools to select Document Viewer (evince) ans the default application for pdf's, used the DEfault Applications for LXSession tool, etc. - all to no avail.

I can open the pdf's using the context menu and selcting Document Viewer, but checking the "set selected application as default for this file type" seems to have no effect the next time I try to double-click on a pdf file (even the same one). I still have to manually select the application. Even using the custom command line tab results in the same thing - the file association does not stick. Logging out and back in, or even rebooting has no effect.

I notice that if I right click to get the context menu and select "properties", there is nothing listed in the "Open with" block, and I only get "Customize" for the drop-down. ??? In addition, if I click the "Cancel" button, I get this error: "No default application is set for MIME type application/pdf".

I'm sure I've made some type of mistake while editing (or even creating) files in the terminal in an attempt to fix this issue, but since I'm relatively new to lubuntu, I don't know where to go next. I wish I would have kept track of exactly what I did at each step, then I could explain. Any help is greatly appreciated! Thanks!

---

### Post by beep3 on 2014-12-31
Sounds like there's something wrong with the PDF (the FF PDF viewer isn't great). Have you checked if the same happens with other PDF documents? You can always quickly create a PDF using LibreOffice and check what's under Properties, Open With.

---

### Post by beep3 on 2014-12-31
You can also check if your system recognises the file as a PDF document with the 'file' utility. Open a terminal, cd to the file and do:

```
file name-of-the-file.pdf
```

The output should be something like: *PDF document, version x.x*

---

### Post by kenneth_myers2 on 2014-12-31
@beep3 - I tried your suggestion, but that doesn't seem to work, no matter how I try to use that command in combination with the actual filename (I tried multiple files, and listed the filename "as-is" as well as with dashes separating the word in the filename).

I put my usb key in and tried some additional pdf files that I can open with no issue on another machine I have that is running Lubuntu 12.04; no issues on that machine, they all open fine by double-clicking on them. Not on my primary machine though. I also installed qpdfview on the affected machine, and though I can open it using that application by right-clicking and selecting it from the context menu (which, btw, Document Viewer is not listed in the context menu, but GIMP, Imagemagick and qpdfview are) it opens fine, but NOT if I double-click the file. Double-clicking results in opening with GIMP.

To me, this seems like a simple file association issue; the problem is, I can't figure out why this happened or how to fix it. Nothing that I've tried that SHOULD set evince as the default app has worked. Why won't it set it as the default when I check-mark that box? Makes no sense.

---

### Post by vasa1 on 2014-12-31
I wonder if your problem is caused by installing GIMP. GIMP isn't part of Lubuntu. I don't have GIMP and don't have any problem opening pdf files.

Anyway, see if [Elfy's solution]("http://ubuntuforums.org/showthread.php?t=2250940&p=13158046#post13158046") works for you. You may want to use gksudo instead of pkexec (if that doesn't work) and leafpad (Lubuntu's default) instead of mousepad.

---

### Post by Rex Bouwense on 2014-12-31
GIMP is installed by default in Lubuntu 14.04.  However, that should have nothing to do with PDF's.

---

### Post by vasa1 on 2014-12-31
> **Rex Bouwense said:**
> GIMP is installed by default in Lubuntu 14.04. ...
No, it isn't: [http://packages.ubuntu.com/trusty/lubuntu-desktop](http://packages.ubuntu.com/trusty/lubuntu-desktop)

---

### Post by kenneth_myers2 on 2014-12-31
@vasa1 - I already did the fixes in that thread, and evince is associated to pdf's already (application/pdf=evince.desktop). Gimp wasn't listed there anyway, if I remember correctly. As a matter of fact, I don't think this started after I installed GIMP. To be honest though, I'm not really sure what caused this issue, as I've been installing new packages and tweaking things on an almost daily basis on this particular machine.

I did recently have to recover the system from my stupidity (I deleted PCManFM, which in turn broke my otherwise great Lubuntu install - and yes, a warning message popped up about removing additional packages lubuntu-core and whatnot, which I ignored), and ever since I've been trying to get things back to the way they were. I have noticed a few issues, one of which is my cpu temps seem noticably higher than they used to be. So, since I've already spent a good 3+ hours messing with this one issue, and my concerns that the install is not the same as it was before my boneheaded move of removing PCManFM, I'm thinking I will just backup my files and do a fresh install of LXLE 14.04 instead.

---

### Post by schragge on 2014-12-31
Please run
```
xdg-mime default evince.desktop application/pdf
```
Then check that it worked with
```
xdg-mime query default application/pdf
```

---

