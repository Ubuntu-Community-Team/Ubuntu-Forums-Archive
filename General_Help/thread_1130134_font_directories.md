---
title: "font directories"
date: 2009-04-19
forum: General Help
---

### Post by mringer on 2009-04-19
On my PC (X-Ub 8.04) the command:

sudo find / -xdev -name fonts -print
[password]

produced this output:
 
/etc/fonts
/etc/apparmor.d/abstractions/fonts
/etc/X11/fonts
/root/.local/share/Trash/files/jre1.6.0_06/lib/fonts
/usr/share/playonlinux/etc/setups/fonts
/usr/share/xine/libxine1/fonts
/usr/share/thunderbird/res/fonts
/usr/share/lilypond/2.10.33/fonts
/usr/share/fonts
/usr/share/texmf/fonts
/usr/share/doc/texlive-fonts-recommended-doc/fonts
/usr/share/doc/texlive-base/fonts
/usr/share/doc/texlive-latex-recommended-doc/fonts
/usr/share/doc/texlive-doc/fonts
/usr/share/doc/texlive-math-extra/fonts
/usr/share/texmf-texlive/fonts
/usr/share/vlc/skins2/fonts
/usr/share/cups/fonts
/usr/share/pyshared/reportlab/fonts
/usr/share/a2ps/fonts
/usr/share/ogonkify/fonts
/usr/share/wine/fonts
/usr/local/share/fonts
/usr/lib/python2.5/site-packages/reportlab/fonts
/usr/lib/xulrunner-1.9.0.8/res/fonts
/usr/lib/jvm/java-6-sun/jre1.6.0_10/lib/fonts
/usr/lib/xorg/modules/fonts
/var/cache/fonts
/var/lib/texmf/fonts
/var/lib/defoma/gs.d/dirs/fonts

I think that this is a mess. This is partly my fault because I have
been installing packages & dont know where to put the font files
--I have not seen this documented. Please is there any reason for
fonts to be scattered about like this?  Is there any recognised
place where one should put font files?

Thank you.

---

