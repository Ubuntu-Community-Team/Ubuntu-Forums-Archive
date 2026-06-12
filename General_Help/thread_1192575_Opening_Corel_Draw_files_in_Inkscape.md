---
title: "Opening Corel Draw files in Inkscape"
date: 2009-06-20
forum: General Help
---

### Post by themusicalduck on 2009-06-20
I'm trying to setup a computer for someone so that they can easily open their old .cdr files in inkscape. I was able to associate all files with inkscape, but it doesn't seem to want to render them properly. It'll open the file ok, but text doesn't show anywhere. All the text boxes are visible and in the right locations, but no text is shown inside.

At first I though it might be because of missing windows fonts, so installed msttcorefonts, but that didn't help. I did a bit of research into it and found you needed a packaged uniconverter. So I tried to convert the .rpm file of uniconverter I found into a .deb, but Alien threw out some errors. Then after a bit more research I found it was already in the repos as python-uniconverter. I tried to install it, but turned out it was already installed anyway.

It is Ubuntu 8.10 and the files are from Coreldraw 9.0. Inkscape is latest in the repository.

---

### Post by themusicalduck on 2009-06-20
bump

---

### Post by zvacet on 2009-06-20
Read [this]("https://answers.launchpad.net/inkscape/+question/55659"),maybe it will be helpful.

---

### Post by themusicalduck on 2009-06-28
Thanks for the link.

I had a look through and tried a few things, but stumbled at trying to install the latest version of uniconverter with alien. I get the error message

Unpacking of 'uniconvertor-1.1.4-1mdv2009.0.i586.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 155.

The same error as the poster in that link, though trying to fixing broken packages and completely removing/reinstalling alien didn't help.

I even tried installing it from source, but gcc gave errors.

---

### Post by themusicalduck on 2009-06-29
bump

---

### Post by maxim2 on 2009-07-06
**UniConvertor Roadmap**

**version 1.1.5**

 
[LIST]
[*]XAR importer (Xara LX graphics format)
[*]CDR exporter (Corel Draw v7 and v11)
[*]DXF exporter (AutoCAD document exchange format)
[*][COLOR=Magenta]text support for CDR importer (Corel Draw v7-12,X3,X4)[/COLOR]
[/LIST]

---

