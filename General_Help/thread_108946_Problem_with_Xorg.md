---
title: "Problem with Xorg"
date: 2005-12-27
forum: General Help
---

### Post by vojtek on 2005-12-27
Hi, 

I have a problem with running Xorg on my computer. From 3 days I was configuring my new system (Ubuntu with KDE). Everyting was ok, until couple hours ago. I was copying files from my windows partition (ntfs) and on 90% system crashed. Only what Can I did was restart..

After restart were many errors. I have done fsck and again restart. File system is now ok, but KDE is not working for me. 

Log (/var/log/kdm.log):

```
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
```

But.. KDE works if I write "startx" as root. For root everything is ok - KDE/Xorg works fine. I have deleted many files from /home/myuser, I deleted that catalog and make it again (without files) - still error. I have done dpkg-reconfigure xserver-xorg - didn't help.

I have completly no idea, what can I do now. I searched on Google, forums, mailing lists. I dont know, why X works for root, but for myuser - no.

I also remember, that after first restart I have error about /etc/console/boottime.kmap.gz - but this error dissapear.

Please help me. Sorry for my english, I hope You can understand, what I have written.

---

### Post by gnu2tux on 2005-12-27
It could be a problem with your preference files. For test purposes drop down to ctrl+alt+f2 (text prompt) log in and do this:

```

cd /
mkdir /home/myuser-old
mv /home/myuser/* /home/myuser-old

```

Basically, this will leave an empty folder for your home system (whilst preserving all your original stuff in the old folder, so you can move it back in if you need to).

Try and start up now - any luck?

If not, can you send us your complete X error log - you can find it in /var/log/X11/Xorg.log (it will be the most recent file in there)

Thanks.

---

### Post by vojtek on 2005-12-27
Hi, thanks for reply

[QUOTE=gnu2tux]Basically, this will leave an empty folder for your home system (whilst preserving all your original stuff in the old folder, so you can move it back in if you need to).
Try and start up now - any luck?[/quote]

I have already done this - still doesn't working.

[QUOTE=gnu2tux]If not, can you send us your complete X error log - you can find it in /var/log/X11/Xorg.log (it will be the most recent file in there)[/QUOTE]

I upload this file here: [http://plikieti.info/Xorg.0.log](http://plikieti.info/Xorg.0.log)

Maybe more info about my system: I installed ati drivers (fglrx, with tutorial from this forum) and I'm using "Splashy". I dont know, if it is important, but better if I write this.


Thanks

---

