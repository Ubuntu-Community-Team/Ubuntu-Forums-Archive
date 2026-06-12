---
title: "Highlighted text becomes totally black in abiword and document viewer (xfce"
date: 2012-07-17
forum: Desktop Environments
---

### Post by afeasfaerw23231233 on 2012-07-17
I am using Xubuntu 12.04 with 'clearlooks' theme. When selecting text in abiword and document viewer (pdf), the text and the blackground of the text turn to black colour (see attachment). But in other applications such as firefox, leafpad, gedit, etc, text highlighting is okay. 

I have tried other theme and found out only 'bluebird' and 'greybird' don't have this problem. However I really don't like this two themes. Any suggestion?

Thanks in advance! 

[ATTACH]221384[/ATTACH]
[ATTACH]221385[/ATTACH]

---

### Post by Toz on 2012-07-17
Clearlooks is a GTK2-only theme and it looks like AbiWord has made the switch to GTK3. None of the gtk2 hacks seem to make a difference.

There is a GTK3 port of the Clearlooks theme [here]("http://www.jpfleury.net/en/software/clearlooks-phenix.php"). It looks very similar to the GTK2 clearlooks but works better with Abiword (not perfect but better - see last statement in this post about Abiword issues) and other GTK3 apps. For Xubuntu 12.04, make sure you download the Clearworks-Phenix 2 version found in the "manually" section.

Keep in mind that the abiword version shipped with 12.04 has many issues. See:
[http://ubuntuforums.org/showthread.php?t=2027325&highlight=abiword]("http://ubuntuforums.org/showthread.php?t=2027325&highlight=abiword")

---

### Post by afeasfaerw23231233 on 2012-07-27
Thank you!

---

