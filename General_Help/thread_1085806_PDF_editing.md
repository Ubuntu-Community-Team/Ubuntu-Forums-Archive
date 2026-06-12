---
title: "PDF editing"
date: 2009-03-03
forum: General Help
---

### Post by coldcoffee on 2009-03-03
I am looking for an application that will allow you to open up pdf forms and edit them. I have a a pdf form that I need to fill in information on and send it somewhere.

Thank you very much

---

### Post by albandy on 2009-03-03
Try pdfedit
sudo apt-get install pdfedit

---

### Post by HermanAB on 2009-03-03
When all else fails, I use The Gimp to edit PDFs.  It is a bit of an annoyance to get the fonts to match, but it can be done in a pinch.

Cheers,

Herman

---

### Post by Rallg on 2009-03-03
Sounds like you just want to fill in forms, rather than edit PDF. You can try Adobe Reader, which has a native Linux version. You have to get it from the Adobe site.

Adobe Reader is available as an RPM file, rather than as a DEB. Currently, the native Linux version is 8.13 even though the Windows/Mac versions are later, but that seems OK. To install an RPM in Ubuntu, you first have to convert it to DEB format, using the "alien" program, available via Synaptic Package Manager. The conversion takes awhile to work. Open a Terminal, navigate to where the *.rpm file is located, then:

sudo alien --scripts name-of-the-deb-file.deb

and after awhile, you will get an installable *.deb file. Do not close the Terminal window (you can minimize it) until you see a new prompt, indicating that conversion is complete.

To install the *.deb you probably need root privileges. It can be done via Terminal commands, but I like graphics, so I do it this way:

sudo nautilus

where nautilus is the file manager in Ubuntu (not Kubuntu or Xubuntu). A window opens, I navigate UP to the top level of the file system, then DOWN to where I put the *.deb file, which might be /home/myusername/Desktop. Then, I can install it using Gdebi package installer (that's the default right-click menu choice).

If you really want to edit a PDF, there is a "pdfedit" program available via Synaptic. It won't do everything.

---

### Post by gandalf2000 on 2009-03-24
I went to the Adobe site to follow the directions Rallg gave and found that there is now a .deb package which I downloaded and installed with Gdebi.  And it appears to be working fine.  Thanks to Rallg.

---

### Post by kaibob on 2009-03-24
> **gandalf2000 said:**
> I went to the Adobe site to follow the directions Rallg gave and found that there is now a .deb package which I downloaded and installed with Gdebi.  And it appears to be working fine.  Thanks to Rallg.
I was curious and checked the version of Adobe Reader available from the Adobe site and the version available with Synaptic from the Medibuntu repository. They are both version 8.13. I don't know of any advantage of Synaptic versus downloading a DEB, but Medibuntu is an alternative source for those who prefer this route.

---

