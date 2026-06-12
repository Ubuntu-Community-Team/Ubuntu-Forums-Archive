---
title: "GTK 1.2 Fonts - i have an idea"
date: 2004-11-13
forum: Desktop Environments
---

### Post by Pawel on 2004-11-13
Hi!

I also have problems with gtk fonts. Yesterday i discovered how to change font size in gtk, but i still dont't understand some things. But at first i 'll show you, how to change your font size :-).

1. In textmode login as root user, and run midnight Commander. You may also run Gedit with root permisions. It's your choice ;-)
2. Go to /etc/gtk/ directory and find the file gtkrc.iso-8859-2
3. Now, change the last line:
form: 
> class "GtkWidget" style "gtk-default-iso-8859-2"
to:
> class "GtkWidget" style "user-font"

Now run xmms, or sth. else wich uses GTK 1.2.

This file in my configuration looks like this:


> #$(gtkconfigdir)/gtkrc.iso-8859-2
#
# This file defines the fontsets for iso-8859-2 encoding
# make symliks or hardlinks to gtkrc.$LANG if your language uses iso-8859-2
# and a gtkrc.$LANG doesn't exist yet.

style  "**gtk-default**" {
       fontset = "-*-helvetica-medium-r-normal--24-*-*-*-*-*-iso8859-1,\
                  -*-arial-medium-r-normal--24-*-*-*-*-*-iso8859-1,\
		  -*-helvetica-medium-r-normal--24-*-*-*-*-*-iso8859-2,\
		  -*-arial-medium-r-normal--24-*-*-*-*-*-iso8859-2,*-r-*"
}
class **"GtkWidget"** style "**user-font**"

When you change bolded parameters, you will see that apps. which uses gtk 1.2 don't change the font size and charset of code page :(. The fonts will be bigger than orginal, but for example - I cant' see polish characters:
[http://schemacik.alternatywa.info/pliki/xmms_ubuntu_gtk.png](http://schemacik.alternatywa.info/pliki/xmms_ubuntu_gtk.png)
Maybe you have some ideas for this problem - how too configure fonts for GTk 1.2 in Ubuntu ?

Best Regards
P.S. Sorry for my english  :-P

---

### Post by free on 2004-11-16
You should install proper fonts for iso-8859-2 (mutatis mutandis for other language). I suppose  these will be ok for you:

   * xfonts-base-transcoded
   * xfonts-75dpi-transcoded
   * xfonts-100dpi-transcoded
   * xfonts-biznet-base
   * xfonts-biznet-75dpi
   * xfonts-biznet-100dpi

Now you can go back to default gtkrc.iso-8859-2.

..at least, it works on my chocolate thing :)

---

### Post by Pawel on 2004-11-28
Hi,

Sorry, but it doesn't help  :neutral: 

Anyway - thanks for your  advice  :-)

---

### Post by nocturn on 2004-12-23
[QUOTE=Pawel]Hi,

Sorry, but it doesn't help  :neutral: 

Anyway - thanks for your  advice  :-)[/QUOTE]

Maybe the solution only works if you are in a certain locale.
I'm in Europe, using 8859-15.
I'm going to try installing the fonts when I have the time.

---

### Post by acidnoizz on 2005-02-01
I have changed the first two lines in "gtk-default" style declaration, and it worked.
Pawe&#322;, napisz&#281; to po angielsku &#380;eby inni te&#380; co&#347; z tego wynie&#347;li :P

My .gtkrc.iso-8859-2 looks like this:

> 
#$(gtkconfigdir)/gtkrc.iso-8859-2
#
# This file defines the fontsets for iso-8859-2 encoding
# make symliks or hardlinks to gtkrc.$LANG if your language uses iso-8859-2
# and a gtkrc.$LANG doesn't exist yet.

style  "gtk-default-iso-8859-2" {
       fontset = "-*-helvetica-medium-r-normal--10-*-*-*-*-*-iso8859-2,\
                  -*-arial-medium-r-normal--10-*-*-*-*-*-iso8859-2,\
		  -*-helvetica-medium-r-normal--10-*-*-*-*-*-iso8859-2,\
		  -*-arial-medium-r-normal--10-*-*-*-*-*-iso8859-2,*-r-*"
}
class "GtkWidget" style "gtk-default-iso-8859-2"
#class "GtkWidget" style "user-font"


I looked at it once more after changing it the way you suggested. I thought that the first declared font is used, so I changed their encoding and it worked perfectly. Also, changing the font size in "gtk-default" worked flawlessly. :)
However, the additional locale fonts should be installed too.

Regards,
Acid

---

### Post by Pawel on 2005-02-10
> **acidnoizz][...]
Pawe&#322 said:**
> 

:> - Moze sie wreszcie doczekamy polskiego wsparcia dla Ubuntu :> - swoja droga to juz cos sie szykuje - a sam chetnie bede wspieral, bo co cieco juz sie nauczylem ;) 
A wracajac do tematu:

International fonts in GTK 1.2 works nice when we truly (as it wrote **free**) - download and install internationalized packeges with fonts for our system.
At least: we don't have to edit gtkrc.//codepage// - files because - fonts should works correctly. In my system i have installed these fonts:

- xfonts-100dpi
- xfonts-100dpi-transcoded
- xfonts-75dpi
- xfonts-75dpi-transcoded
- xfonts-base
- xfonts-base-transcoded
- xfonts-biznet-100dpi
- xfonts-biznet-75dpi
- xfonts-biznet-base
- xfonts-biznet-iso-8859-2-100dpi
- xfonts-biznet-iso-8859-2-75dpi
- xfonts-biznet-iso-8859-2-base

And BTW:
- xfonts-scalable
--------
- gtkfontsel
------------------
For future:
- qte-fonts ;)
- gsfonts
- gsfonts-X11



After instalation these packeges - we have to restart our system (or not - anyway - after reboot we can see changes). Fonts in apps based on GTK 1.X should works correctly :-)

Best regards
Pawel W.

---

### Post by watchitman on 2005-03-01
I wasn't able to follow any of this. I've been asking how to fix the fonts in another thread for a month now and no one answers. Could someone please explain this so even a dummy can understand?

---

### Post by wassermann on 2006-01-01
Hello,
first many thanks to Pawel. This solution works fine for me. I think there is only one thing to look for : You have to be sure to take the file according to your default locales, in my case it was 8859-15 for de_DE@euro.

best regards

---

