---
title: "Alternative to kpdftool"
date: 2008-07-19
forum: Desktop Environments
---

### Post by crazy ivan on 2008-07-19
In my studies I often need to merge, cut and extract PDF files. [Kpdtool]("http://www.kde-apps.org/content/show.php?content=33194") used to be a really cool app to do this in my SUSE times. But development on it seems to have come to a premature end and there are no packages for ubuntu. Are there any GUI driven alternatives somewhere to be found - preferably GNOME?
I know there is this comandline tool "pdftk", but I don't use it as much that I could memorize the syntax.. At the moment I just print pages to PDF when I want to extract something. With merging I'm helpless.

---

### Post by crazy ivan on 2008-07-20
Nice thing would also be rotating pages by 90°

---

### Post by DrHu on 2008-07-21
[quote=crazy ivan]In my studies I often need to merge, cut and extract PDF files. Kpdtool used to be a really cool app to do this in my SUSE times. But development on it seems to have come to a premature end and there are no packages for ubuntu.[/quote]
**You can/can't use kde applications in Gnome/Ubuntu ? [color=navy]Why not keep using kpdftool[/color]**
--I thought they had fixed their integration issues

There is also something like scribus (a dtp package), but not for working directly on a pdf file (but able to open it), you could cut & paste from the data once it was opened and save the results to a new page, then create that as a pdf
[http://docs.scribus.net/index.php?lang=en&page=examples/cgiform/pdf_form](http://docs.scribus.net/index.php?lang=en&page=examples/cgiform/pdf_form)
[http://www.tuxmagazine.com/node/1000225](http://www.tuxmagazine.com/node/1000225)
[http://www.scribus.net/](http://www.scribus.net/)

And there is also something 
[http://sourceforge.net/projects/gscan2pdf](http://sourceforge.net/projects/gscan2pdf)
--creating a pdf file from scans

---

### Post by crazy ivan on 2008-12-25
Thanks for the good links DrHu.. With scribus one could do the stuff on PS/EPS but they can't import PDF yet.
For me I came to a simple and very effective solution for merging PDFs:
1) get the wonderfull rpm > deb converter alien
```
 sudo apt-get install alien 
```
2) get the "kpdftool-0.22-10.1.i586.rpm" for Opensuse 10.1 from [ rpmseek.com ]( rpmseek.com )
3) do the conversion
```
 sudo alien kpdftool-0.22-10.1.i586.rpm 
``` or more secure
```
 fakeroot alien kpdftool-0.22-10.1.i586.rpm 
```
4) install
```
 sudo gdebi kpdftool-0.22-10.1.i586.rpm 
```
5) execute (not listed in menu) an enjoy
```
 kpdftool 
```

---

