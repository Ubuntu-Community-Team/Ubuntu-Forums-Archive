---
title: "Adobe acrobat"
date: 2007-08-28
forum: Education &amp; Science
---

### Post by ntlam on 2007-08-28
Can we install adobe acrobat on feisty or is there any similar program that I can use to create pdf files?

Thanks

Lam

---

### Post by in_flu_ence on 2007-08-28
The only one that I use for pdf creation is openoffice if that fits your need.

---

### Post by tweedledee on 2007-08-29
> **ntlam said:**
> Can we install adobe acrobat on feisty or is there any similar program that I can use to create pdf files?

Thanks

Lam

To create pdfs in general, otuside of openeoffice and the few other programs that explicitly allow it, install cups-pdf.  It sents up a pdf printer that you can use instead of Acrobat/Distiller.

---

### Post by ntlam on 2007-08-29
Thanks

It seems that I have some options.

---

### Post by MJWhiteDerm on 2007-08-29
The next question then becomes, how to install CUPS-PDF .... I tried installing a new printer, figuring that PDF would be an option.  I then installed CUPS Printer Manager, figuring that would have it as an option, and it doesn't.

Finally, I went to the synaptic package manager, where cups-pdf is a package one can install.  I did that.

When you print to the cups-pdf, you must check the little box that make the system save it as a file.   Unlike Adobe Acrobat, it doesn't automatically do this.  I have just printed one of the how-to's from the forum, using PDF-Writer (which is what I chose to call the cups-pdf virtual printer thus created) and then saved the file.  I subsequently opened the file and am printing it out.

This should provide the ability to make PDF files when you are not in OpenOffice.

---

### Post by ntlam on 2007-08-29
> **MJWhiteDerm said:**
> The next question then becomes, how to install CUPS-PDF .... I tried installing a new printer, figuring that PDF would be an option.  I then installed CUPS Printer Manager, figuring that would have it as an option, and it doesn't.

Finally, I went to the synaptic package manager, where cups-pdf is a package one can install.  I did that.

When you print to the cups-pdf, you must check the little box that make the system save it as a file.   Unlike Adobe Acrobat, it doesn't automatically do this.  I have just printed one of the how-to's from the forum, using PDF-Writer (which is what I chose to call the cups-pdf virtual printer thus created) and then saved the file.  I subsequently opened the file and am printing it out.

This should provide the ability to make PDF files when you are not in OpenOffice.

Thanks 

Did you send me a message? I couldn't see the content of the message. Even my old messages had no content. I dont know what's wrong with that.

---

### Post by tweedledee on 2007-08-30
> **MJWhiteDerm said:**
> The next question then becomes, how to install CUPS-PDF .... I tried installing a new printer, figuring that PDF would be an option.  I then installed CUPS Printer Manager, figuring that would have it as an option, and it doesn't.

Finally, I went to the synaptic package manager, where cups-pdf is a package one can install.  I did that.

When you print to the cups-pdf, you must check the little box that make the system save it as a file.   Unlike Adobe Acrobat, it doesn't automatically do this.  I have just printed one of the how-to's from the forum, using PDF-Writer (which is what I chose to call the cups-pdf virtual printer thus created) and then saved the file.  I subsequently opened the file and am printing it out.

This should provide the ability to make PDF files when you are not in OpenOffice.

It doesn't need to be that complicated: [http://ubuntuforums.org/showthread.php?t=188860](http://ubuntuforums.org/showthread.php?t=188860)

---

### Post by ntlam on 2007-08-31
> **tweedledee said:**
> It doesn't need to be that complicated: [http://ubuntuforums.org/showthread.php?t=188860](http://ubuntuforums.org/showthread.php?t=188860)

I follow instruction in that thread but it did not work.
As it said:
# Open a terminal and tpe "sudo nautilus" and then your password
# Go to Filesystem -> usr -> lib -> cups -> backend
# Rightclick "cups-pdf" and select Properties
# Go to the Permissions tab and click the "Set user ID" special flag

I did not see "set user ID" when doing that.

---

### Post by ntlam on 2007-08-31
I already installed cups-pdf but it doesnt seem to exist when I test printing.

---

### Post by tweedledee on 2007-08-31
> **ntlam said:**
> I already installed cups-pdf but it doesnt seem to exist when I test printing.

I would suggest posting on the HOWTO thread instead of here (or at least in addition), as you are more likely to find someone who can help you troubleshoot.  Regarding the permissions issue, there is a way to change which set of options Nautilus displays for setting permissions, but it escapes me at the moment (possibly using gconf-editor).  An alternative method to what you copied above is to just open a terminal, navigate to that directory, and type
```
su chmod +s cups-pdf
```

---

### Post by edoviak on 2007-09-02
There are several options.
[LIST=1]
[*]As previously mentioned, **OpenOffice** allows you to export to PDF.
[*]As previously mentioned, **cups-pdf** allows you to print to PDF and pick up the PDF file from a PDF folder in your home directory.
[*]You can print to a postscript file and then use **ps2pdf** (from the command line) to convert the PS to a PDF.
[*]If you use Kubuntu, then **Kprint** will give you an option to print to PDF (for some programs anyway).
[*]**pdftk** (from the command line) helps you merge several PDF files, remove pages from a PDF file, etc.
[*]Finally, to edit the text of PDF documents, merge PDFs, etc., you can use **PDFedit**. It's a bit more like Adobe Acrobat in that it has a graphical user interface (GUI), but it's still in development (and has to implement the standards set on high from Adobe).
[/LIST]
The combination of options discussed above provide me with almost all of the PDF functionality that I need. 

The only time I ran into trouble was when I had to complete a bunch of PDF forms for my wife's green card application. Given the choice of seeing my wife deported or using proprietary software (Adobe) to get the job done, I chose to deport my wife. It was sad to see her go, but freedom is that important to me!

Hope this helps,
- Eric

ps: Obviously, I'm joking! ... but the point is nonetheless valid. Why does a government agency require its citizens to use expensive proprietary software, like MS Word, MS Excel and Adobe Acrobat?

---

