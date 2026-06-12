---
title: "Rendering doc(x)"
date: 2021-06-28
forum: Desktop Environments
---

### Post by xinuzi on 2021-06-28
Hello,

Don't know if this is the right place to place it, but this is my case:

The government sent me a Microsoft doc-document to sign. 

Due to bad editing or due to too many phantasies in the editing this document didn't show well at all in libreoffice on a Ubuntu 20.04 system with Lubuntu LXQT.

The program AbiWord gave better results, but not ideal.

The document rendered better on another system with Linux Mint, but still not what one would expect.

The problem was not only the Microsoft Only fonts, but above anything the fact that the office-clerk-editor, had mixed landscape (horizontal) and potrait (vertical) pages within the document.

I looked in Synaptic Package Manager with the search term 'libreoffice' if there was anything I could add to make things better. In vain. 

The link with Desktop Environments is maybe the difference in rendering of the doc with libreoffice between Lubuntu (LXQT) and Linux Mint (v 19)?
Both use ubuntu.

---

### Post by cmcanulty on 2021-06-28
First you can add Microsoft fonts easily. Look for the package 

[https://itsfoss.com/install-microsoft-fonts-ubuntu/]("https://itsfoss.com/install-microsoft-fonts-ubuntu/")

Also look at only office. It claims to be the most closely tied to Microsoft office rendering, deb file is toward bottom of page. All free

[https://www.onlyoffice.com/download-desktop.aspx?from=desktop]("https://www.onlyoffice.com/download-desktop.aspx?from=desktop")

---

### Post by xinuzi on 2021-06-29
In the meantime I've tested 'onlyoffice' on Lubuntu LXQT - ubuntu 20.04 X64, cmcanulty.

The 'Debian 8, Ubuntu 14.04 and higher' deb installed, but was nowhere to be found on the system afterwards.

The AppImage does work, but slow.

Both rather large files/packets.

The original government doc opened in the AppImage, gave a slighlty better view, but still poor.

I had reedited that document in libreoffice on Linux Mint the best way possible before anyway - and had saved it as pdf.

But, this was interesting to know if the bad layout was caused by the original clerk-editor or by the current Linux system(s)/environments.

I could 've, but didn't, check the government document on Windows 10, but was too lazy for that ;-)
(Maybe I should)

You would expect The Government to provide universally compatible documents to its citizens.

Not only the Microsoft Only fonts cause doc(x) to fall apart, but also, as said, too many 'phantasies', badly formatted tables, mixture of horizontal and vertical pages, the line-out.

Thank you for your contribution.

Linux Rox!

---

### Post by monkeybrain20122 on 2021-06-29
> **xinuzi said:**
> 

You would expect The Government to provide universally compatible documents to its citizens.


Hahaha, this is the last thing you should expect from governments unless there is a big push from the top like the U.K government has banned the use of MS only formats (docx , xlsx etc) some years ago, otherwise the old timers just stick to old tech they are familiar with and require least work. Not too long ago many government websites required internet explorer and with luck you maybe able to access them with Firefox using an agent switcher. This was completely unnecessary. I guess those are no more now that even MS doesn't support IE.

---

### Post by entropy1 on 2021-06-30
After installing
```
ttf-mscorefonts-installer
```
I would also install
```
fonts-crosextra-caladea
fonts-crosextra-carlito
```
which are metrically compatible with Cambria and Calibri (i.e., won't change linebreaks, etc.).

Alternatively, if you have a hotmail or outlook account, you can upload the original .docx file to OneDrive and edit the .docx online and then download it. It's worth creating such an account even for unedited .docx files because after uploading you can view as pdf and download the pdf with the correct fonts and spacing.

---

