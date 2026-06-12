---
title: "How to change hyperlink color?"
date: 2009-04-03
forum: General Help
---

### Post by taqkavar on 2009-04-03
Hello everyone
I have been looking for a way to change the default hyperlink colour in gnome from blue to orange, no matter where I look can't find where to tweak this.
If anyone knows how to please help.
Thank you.

---

### Post by mb_webguy on 2009-04-03
Install the gnome-color-chooser package.  This will allow you to easily change the colors used by Gnome for various things, including hyperlinks (at least in the most recent version).

---

### Post by taqkavar on 2009-04-05
Thanks, I did try the latest gnome-color-chooser, but it did not change hyperlink colors in Evolution like I wanted it to. After looking around a bit more I was able to find out that gnome-colour-chooser basically modifies ~/.gtkrc-2.0 , after adding some stuff to this config file I was finally able to change most hyperlink colors. Here is the contents of mine:

#--------------------------------------------------------
style "default-style"
{
  GtkWidget::link-color = "#acee00"
  GtkWidget::visited-link-color = "#ffc100"
  GtkHTML::alink_color = "#acee00"
  GtkHTML::link_color = "#acee00"
  GtkHTML::vlink_color = "#ffc100"
  GnomeHref::link_color = "#acee00"
  GtkIMHtml::hyperlink-color = "#acee00"
  GtkIMHtml::hyperlink-prelight-color = "#ffc100"
}

class "GtkWidget" style "default-style"
#---------------------------------------------------------

gnome-color-chooser only uses "GtkWidget::link-color" and "GtkWidget::visited-link-color" to change hyperlink colour but it seem evolution and some other applications use GtkHTML, GnomeHref or GtkIMHtml. Unfortunately look like Tomboy uses none of the above and is still displaying links in blue.

---

### Post by Fenboy on 2009-05-13
Many thanks for that.  Your fix has made a dark theme usable.

---

### Post by Vermind on 2009-05-25
It would appear that Tomboy has a class called Contrast.cs, which hard-codes a set of "appropriate" colors. Then, the NoteTag.cs class similarly hard-codes which colors to use for which note tags. I would think that people want more choice than this.

Anyway, the default color for titles and links is Blue. I changed it to LightBlue. [Deb package attached]("http://dl.getdropbox.com/u/971117/dev/tomboy_0.15.0-1_i386.deb") ( via [Dropbox]("https://www.getdropbox.com/referrals/NTk3MTExNzk") )

Alternatively, go to the [Tomboy website]("http://projects.gnome.org/tomboy/download.html"), and download the tarball. Extract it, and go to the Tomboy subdirectory. edit NoteTag.cs so that the colors are something that sounds appropriate, keeping Contrast.cs open for color name reference. Then save, and run the usual ```
./configure --prefix=/usr && make && sudo make install
``` in the extracted directory. If You never built tomboy before, you will need to ```
sudo apt-get build-dep tomboy
``` to be able to get through ./configure.

---

### Post by motosauro on 2010-09-16
> **taqkavar said:**
> Thanks, I did try the latest gnome-color-chooser, but it did not change hyperlink colors in Evolution like I wanted it to. After looking around a bit more I was able to find out that gnome-colour-chooser basically modifies ~/.gtkrc-2.0 , after adding some stuff to this config file I was finally able to change most hyperlink colors. Here is the contents of mine:

#--------------------------------------------------------
style "default-style"
{
  GtkWidget::link-color = "#acee00"
  GtkWidget::visited-link-color = "#ffc100"
  GtkHTML::alink_color = "#acee00"
  GtkHTML::link_color = "#acee00"
  GtkHTML::vlink_color = "#ffc100"
  GnomeHref::link_color = "#acee00"
  GtkIMHtml::hyperlink-color = "#acee00"
  GtkIMHtml::hyperlink-prelight-color = "#ffc100"
}

class "GtkWidget" style "default-style"
#---------------------------------------------------------

gnome-color-chooser only uses "GtkWidget::link-color" and "GtkWidget::visited-link-color" to change hyperlink colour but it seem evolution and some other applications use GtkHTML, GnomeHref or GtkIMHtml. Unfortunately look like Tomboy uses none of the above and is still displaying links in blue.

Thanks from me too: I also had the problem of a dark theme unusable (I'm in kde4 with QtCurve for gtk Apps)

---

### Post by lukanova on 2011-01-03
> **Vermind said:**
> It would appear that Tomboy has a class called Contrast.cs, which hard-codes a set of "appropriate" colors. Then, the NoteTag.cs class similarly hard-codes which colors to use for which note tags. I would think that people want more choice than this.


i find it totally insane that these colors are hard-coded. any dark theme fails miserable with tomboy and renders it unusable.

---

### Post by Vaphell on 2011-01-03
many devs lack foresight and if it works for them then it works for everyone, right? :-) laziness can be another reason, hardcoding is simple, fooling around with gtk properties not so much

---

### Post by Vermind on 2011-01-03
Old thread.
Nowadays some dark themes such as DarkRoom and DarkLooks essentially give up; they only use a dark background for non-input areas and use a light background with black text for input areas.
I have learned to live with them, since it seems to be the only way. Also a lot of websites force a light background theme, and dark themes dont help there.

I use the compiz negative plugin to read PDFs in negative, but websites generally don't look good in negative.

Any ideas for websites?

---

