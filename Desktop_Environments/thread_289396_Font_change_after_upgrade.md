---
title: "Font change after upgrade?"
date: 2006-10-30
forum: Desktop Environments
---

### Post by EvergreyNY on 2006-10-30
After upgrading to Edgy Eft, the fonts for the settings in XMMS and all the fonts in Audacity are very... well, crappy looking. They both were set to the correct font size (8pt) before I upgraded and now I can't get them to look normal.

[[IMG]http://img167.imageshack.us/img167/7995/textpz9.th.png[/IMG]](http://img167.imageshack.us/my.php?image=textpz9.png)

So far it's just these two applications that I have run across with this problem so far.](*,)

---

### Post by DonVla on 2006-10-31
hello,

you can try "switch" (package "gtk-theme-switch"), but it didn´t work for me.
the fonts under edgy are quite annoying!!!

vlad

---

### Post by Miguel on 2006-10-31
I don't think it's a theme issue. XMMS is a gtk+ 1.2 app, so one might think it's related to a gtk+ (not gtk2, used by the rest of gnome/xfce) issue. But then I browsed the audacity web and found that it uses wxWidgets. This is starting to get interesting.

But then, I have compiled a beautiful tool for my work, called XCrySDen. It needs mesa, Tcl and Tk. Apparently nothing to do with the above. Well, check the screenshot. Does it ring a bell? I have tested it with full subpixel hinting, with none and another intermediate option. To no avail. It looks OK on the Debian Etch PC on my left and it looked OK under dapper in this very same laptop. But I don't get what's wrong.

---

### Post by Miguel on 2006-10-31
OK, I've had a look at package dependencies and the reason why audacity also looks bad might be because it uses wxGTK. I think this "translates" some wxWidgets calls into gtk+1.2 (also used by XMMS). Maybe installing a gtk+ theme will help.

However it still doesn't answer why I am getting crappy fonts in a Tcl-Tk app such as XCrySDen. I've just checked, and the help browser of scilab (installed directly from the multiverse repositories) also displays nasty fonts. Scilab also uses tcl-tk. Isn't it great?

---

### Post by EvergreyNY on 2006-10-31
Well, I've just started using another audio player instead of XMMS. I guess I can live with it for now until I figure something out. More of an annoyance than anything. Thanks for the help. I'll let you guess know if I end up with anything.

---

### Post by Miguel on 2006-11-03
What happens if you delete the file ~/.fonts.conf (backup first, just in case)?

---

### Post by DonVla on 2006-11-04
hello,

i got the dapper fontlook back. this works only in firefox (big menu fonts) and gtk2 apps, but not in gtk1 apps like audacity or xmms.
i found this thread:
[http://www.kanotix.com/PNphpBB2-viewtopic-t-21030.html](http://www.kanotix.com/PNphpBB2-viewtopic-t-21030.html)
```
mv /etc/fonts /etc/fonts.backup
apt-get install --reinstall --yes -o DPkg::Options::=--force-confmiss -o DPkg::Options::=--force-confnew fontconfig fontconfig-config
```
and then i changed in my ~/.fonts.conf "hintmedium" to "hintfull" as explained in this thread:
[https://launchpad.net/distros/ubuntu/+source/fontconfig/+bug/63403](https://launchpad.net/distros/ubuntu/+source/fontconfig/+bug/63403)
that worked.
i have no idea how to change the fonts of gtk1 apps.
now i´m not using xmms anymore. give audacious a try. it´s the same as xmms, but based on gtk2.

vlad

---

### Post by DonVla on 2006-11-04
hello,

i found out how to change the gtk1 fonts. in /etc/gtk are the gtkrc files for the given encodings. if you use utf-8 (default in ubuntu), then you have to edit gtkrc.utf-8. 
```
vim /etc/gtk/gtkrc.utf-8
```
therein you can change the fontstyle and size. that worked. 
my /etc/gtk/gtkrc.utf-8:
> style "default-text" {
       fontset = "-*-arial-medium-r-normal--*-90-*-*-*-*-iso10646-1,\
                  -*-helvetica-medium-r-normal--*-90-*-*-*-*-*-*"
}

class "GtkWidget" style "default-text"


vlad

---

### Post by Miguel on 2006-11-14
Hi guys,

Just browsing on the x.org wiki I've found the "answer" to my Tcl/Tk issues. On my system, X didn't correctly detect my monitor's size, setting the dpi at 75dpi. However, my 15.4" laptop should have a 98dpi resolution. Adding the following line
```

DisplaySize     331 207

```
to the "Monitor" section and restarting the X server did the trick. Here you should put your monitor's dimensions in milimetres (25.4 milimetres = 1 inch). You can see the difference in the attached screenshot.

I'll add just a couple of notes:[list=1]
[*]You can check your current X dpi by running the command (needn't be root):
```

grep DPI /var/log/Xorg*

```
[*]I don't know if this will work on GTk 1 apps
[*]The fonts are still not antialiased. This is a feature of Tcl/Tk 8.5.
[/list]

*EDIT:* If this works for GTk 1.2 apps, ***please*** report it, as we can then post it on launchpad as bug workaround or something similar.

---

### Post by DonVla on 2006-11-14
these options do the same:
```
  Option          "UseEdidDpi"   "FALSE"
        Option          "DPI"   "96 x 96"
```
but i don´t think this _is_ the solution.

have you read what i´ve posted before?

vlad

---

### Post by Miguel on 2006-11-14
> **DonVla said:**
> 
Have you read what i´ve posted before?


Yes, I have. Your changes from medium hinting to full hinting is described in launchpad, though I don't remember which of the 72000 bugs was. Accordingly, the gtk2 apps look better. And then you post that gtkrc and I think "Mmmm... msttcorefonts. Maybe it would be better had he used DejaVu or Bitstream Vera." It's not like nobody installs those fonts (it's the other way round) but they are not installed by default.

And trust me I would have tested your solution... but I have no gtk 1.2 app installed and my issues are (were) with Tcl/Tk.

BTW: Your xorg.conf code fixes the DPI. I would recommend to specify the display's size, since this will use large fonts at high resolutions and small fonts at low resolution.

---

### Post by eric_m_allen on 2006-11-20
DonVLA's fix worked for Audacity, but now I have 9 point unsmoothed fonts rather than nice clean smoothed ones that the rest of Gnome uses-if I can find the right font settings I'll post them...

---

### Post by eric_m_allen on 2006-11-20
I think this might be the definitive answer-http://www.ubuntuforums.org/archive/index.php/t-107135.html
I'll try it when I get home-I'm behind a firewall and proxy here at work.

---

