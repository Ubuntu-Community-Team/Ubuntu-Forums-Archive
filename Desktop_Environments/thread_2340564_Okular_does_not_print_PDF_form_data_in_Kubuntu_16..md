---
title: "Okular does not print PDF form data in Kubuntu 16.04"
date: 2016-10-19
forum: Desktop Environments
---

### Post by ericjoh on 2016-10-19
I have tried printing a PDF file containing form data from Okular in both Kubuntu 16.04 and 14.04, but the form fields are blank when printed. Everytime I open this PDF file with Okular I have to click on the "Show Forms" button at the right of the text "This document has forms. Click on the button to interact with them, or use View -> Show Forms." to have the form data shown on screen, but when printing the forms are still blank when it comes out on paper.

I just saw a new comment in [https://bugs.kde.org/show_bug.cgi?id=319163](https://bugs.kde.org/show_bug.cgi?id=319163) that the bug has been around for many years now and is still there. Anyone know a fix/patch to have Okular print form data?

When trying to print this PDF file with forms in macOS with Preview is works as expected and the forms are printed.

Thanks in advance!

(The reason why I do not attach the actual PDF file is because it is an internal document at the organization where I work.)

---

### Post by monkeybrain20122 on 2016-10-21
Instead of save, print and maybe print to a different document. Open in a different PDF viewer still see the content.

---

### Post by accounts0 on 2017-05-13
> **monkeybrain20122 said:**
> Instead of save, print and maybe print to a different document. Open in a different PDF viewer still see the content.

Not working this way.

The only solution I've found is to run a Windows VM & save the completed forms in Adobe Acrobat Pro, after which Okular displays the completed fields.

However Okular won't print the form data unless I check "Force rasterization" in "Print > Options > PDF Options > Force rasterization". Would be nice if I could set that to stay checked by default, but so far I see no way to do so.

EDIT:
I found that if I change the default font used in form fields to "Helvetica" in Adobe Acrobat Pro on Windows, then it prints the filled-in field data by default when I print it in 'qpdfview' in linux.

---

### Post by monkeybrain20122 on 2017-05-14
> **accounts0 said:**
> Not working this way.

The only solution I've found is to run a Windows VM & save the completed forms in Adobe Acrobat Pro, after which Okular displays the completed fields.

However Okular won't print the form data unless I check "Force rasterization" in "Print > Options > PDF Options > Force rasterization". Would be nice if I could set that to stay checked by default, but so far I see no way to do so.

EDIT:
I found that if I change the default font used in form fields to "Helvetica" in Adobe Acrobat Pro on Windows, then it prints the filled-in field data by default when I print it in 'qpdfview' in linux.

I don't have okcular any more but I remember it used to work, except sometimes the filled data don't display correctly when you re-open the filled form (in Okular or other PDF readers, but they do display) Evince, qpdfview and master Pdf-editor all suffer from the same problem(filled data got mangled sometimes) I have not tried but you can probably fix it by changing the fonts or something. 

In any case running Adobe in a VM seems to be overkill. My understanding is that the difficulties of (free) Linux PDF apps in handling certain pdf forms has to do with the open source poppler backend lacking certain proprietary features. If you just want to fill the form running PDF-Xchange viewer in wine would work for all of them.

---

