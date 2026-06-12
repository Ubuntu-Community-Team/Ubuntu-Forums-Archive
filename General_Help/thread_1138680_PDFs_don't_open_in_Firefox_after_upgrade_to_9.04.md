---
title: "PDFs don't open in Firefox after upgrade to 9.04"
date: 2009-04-26
forum: General Help
---

### Post by dhavalbbhatt on 2009-04-26
Hi All,

I upgraded to 9.04 recently and have noticed that I can no longer open PDF documents in Firefox. Anyone else experiencing this issue? How to fix it?

Thanks,
DB

---

### Post by VCoolio on 2009-04-26
I didn't know it was ever possible in firefox. Are you sure you didn't use an add-on for that? Like [this one]("https://addons.mozilla.org/en-US/firefox/addon/636")?

---

### Post by platinumriver on 2009-04-26
I have the same problem. I did not use an add-on. Here's a link to a pdf.

[http://www.vmware.com/pdf/ws6_manual.pdf](http://www.vmware.com/pdf/ws6_manual.pdf)

In my browser, now it is just a blank page. From the 'about:plugins' page, this is what I have.

Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes

---

### Post by dox_drum on 2009-04-26
If you have the MEDIBUNTU repository, try to install mozilla-acroread

```
sudo apt-get install mozilla-acroread
```

---

### Post by peace_v2k on 2009-04-26
I had just recently also upgraded to 9.04. However prior to the upgrade I had downloaded and installed the "Adobe Reader" from Adobe's website. I have no problem viewing PDF's inline. You may want to try that (?)

---

### Post by kansasnoob on 2009-04-26
It works fine for me with evince. I never install adobe/acroread anymore.

---

### Post by Nuked on 2009-05-05
messed around a bit with the medibuntu repositories (which *are* nice) and the mozilla-acroread - but I find it much much easier to just go to the adobe site and download acrobat reader, be sure to choose a "a different OS" and choose x86 Linux .deb and you'll be fine.

---

