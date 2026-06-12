---
title: "Firefox save image as"
date: 2006-11-21
forum: Desktop Environments
---

### Post by canarsie on 2006-11-21
In firefox, when I right click on an image and select "save image as", nothing happens.  If I select properties, I get the following error:

XML Parsing Error: error in processing external entity reference
Location: chrome://browser/content/metaData.xul
Line Number 8, Column 64:<!DOCTYPE window SYSTEM "chrome://browser/locale/metaData.dtd" >
---------------------------------------------------------------^there.is.only.xul">
-----------------^

Has anyone else experienced this or know how to fix it?  Thanks.

---

### Post by Namakemono-san on 2006-11-22
Did you run updates today? I'm having the same issue. I am also having a few other issues with Firefox today. While trying to download a file, the download dialog box comes up, but is missing the text on all of the buttons, and none of them work. I have to exit out of the window and can't download. I was also having trouble getting a login button on a web page to work. 

This all started after I installed some updates for Firefox in the Ubuntu updates box. Something was wrong with the update I think?

---

### Post by Namakemono-san on 2006-11-22
Also, I can't add bookmarks...the add button does not function.

---

### Post by Namakemono-san on 2006-11-22
Running update manager again and installing all updates available fixed the problem for me. Try that.

---

### Post by canarsie on 2006-11-23
yeah that worked.  Thanks.

---

### Post by Teilanus on 2006-11-29
That not worked for me. I have same problem with "save image as", nothing happens. I have Firefox 2.0

---

### Post by ambrosa on 2007-08-08
I've just installed Ubuntu 7.04 (all update applied). Firefox 2 works fine.

Then I've copied my profile from my Windows partition (C:\Document and Settings\myuser\.....) to my Ubuntu home dir ($HOME/.mozilla/firefox/myuser) and channged profile.ini accordingly.
All add-ons, bookmark and so on work fine BUT no more the "Save image as" button (or "save link as" and many other)

Firefox error console shows:
[I]Error: uncaught exception: [Exception... "Component returned failure code: 0x80520001 (NS_ERROR_FILE_UNRECOGNIZED_PATH) [nsIPrefBranch.getComplexValue]"  nsresult: "0x80520001 (NS_ERROR_FILE_UNRECOGNIZED_PATH)"  location: "JS frame :: chrome://global/content/contentAreaUtils.js :: getTargetFile :: line 496"  data: no]
[/I]
I've removed ALL add-ons without success.
I can suppose that in Windows profile there is a Firefox core file that is wrong for a Firefox Linux profile and cannot be simply transferred/copied from Windows to Linux.
Yes, I can use a core file from a Firefox Linux profile, but I don't know which file it is.....

Someone can help me ?

---

### Post by ambrosa on 2007-08-08
Solved myself.

Delete file ***prefs.js*** from your Linux profile folder (saved sites passwords will NOT be deleted).
Aftere the next Firefox run, ***prefs.js*** will be created again with default values.
Obviously you must set again your preferences.

I suppose that in prefs.js copied from Windows profile there are some data not compatible with Linux Firefox.

---

