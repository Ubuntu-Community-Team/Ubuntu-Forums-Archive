---
title: "Acroread plugin for Firefox DOES work"
date: 2008-01-13
forum: Desktop Environments
---

### Post by mount_evans on 2008-01-13
When searching for information about the Adobe Acrobat reader plugin for Firefox, all I found were comments saying that it does not work, or that other alternatives are better.  I went to the following website:

[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html)

...and executed the four commands given there in a terminal window:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update

sudo apt-get install acroread mozilla-acroread acroread-plugins

...and now I can read PDFs in Firefox.  Is there any reason not to use this plugin?  I noticed that Synaptic contained no Acroread packages at all, and wondered what the reason was.  Do any of the alternatives plug in to Firefox and allow you to read "webpages" that are actually PDFs?

I am running Ubuntu 7.10, FWIW.

---

### Post by PeterJS on 2008-01-13
There are license restrictions on the acrobat reader plugin. Canonical can not distribute it as they are subject to US law. Medibuntu however has no such restriction, hence having the acrobat plugin, libdvdcss, w32codecs, etc.

I've never heard of anybody saying not to use the adobe plugin, where'd you hear that. That said I recommend Medibuntu all the time, they do the leg work that Canonical can't because of US law.

---

### Post by peterwr on 2008-01-17
Personally, I've been pleasantly surprised by how well Evince works as a PDF viewer. It doesn't work as a plugin in the browser, but it does download and display documents much more quickly than Adobe  Reader. It's now my default PDF reader (set in FF Prefs > Content > File Types), and I don't miss Reader at all - in fact, since doing a clean install of Gutsy, I haven't bothered re-installing it. YMMV, of course... :-)

Thanks for the info, though - I'll keep it bookmarked in case I ever feel the need for Reader.

---

### Post by kerry_s on 2008-01-17
you could also have used mozplugger. sudo apt-get install mozplugger
mozplugger can put alot of things inside the browser. 
about plugger-> [http://fredrik.hubbe.net/plugger.html](http://fredrik.hubbe.net/plugger.html)

---

