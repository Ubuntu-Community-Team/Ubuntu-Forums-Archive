---
title: "Arabic support for firefox, not rendering correctly"
date: 2009-04-22
forum: General Help
---

### Post by soule on 2009-04-22
Hi,

I'm trying to view the website [COLOR="Blue"][http://quranexplorer.com/quran]("http://quranexplorer.com/quran")[/COLOR](in arabic). But, what happens is that, as seen in the screenshot at the bottom of my post, it has rectangular things with 4 digits in each in place of the letters. However, that is only for about half of the letters, the other half are rendered correctly. I don't get it, it worked when I used to use XP but not anymore. Could anyone help?

-soule (screenshot below)

[IMG]http://souleiman.com/files/arabic_support-forums.png[/IMG]

---

### Post by soule on 2009-04-22
bump, please assist?

---

### Post by soule on 2009-05-01
bump, im desperate.

---

### Post by drpyro on 2009-08-14
no solution yet ? i'm facing same problem with Mozilla Firefox shiretoko/3.5.3pre...

---

### Post by soapBAR2 on 2009-08-14
Do you have the correct fonts installed?

> $ sudo apt-cache search arab | grep font
language-support-fonts-ar - Additional fonts metapackage for Arabic
ttf-arabeyes - Arabeyes GPL TrueType Arabic fonts
ttf-kacst - KACST free TrueType Arabic fonts
ttf-sil-andika - extended smart Unicode Latin/Greek font family for literacy (Basic version)
ttf-sil-scheherazade - smart Unicode font for Arabic
emacs-intl-fonts - Fonts to allow multi-lingual PostScript printing from Emacs
xfonts-efont-unicode - /efont/ Unicode fonts for X which cover various scripts
xfonts-efont-unicode-ib - /efont/ Unicode fonts for X (italic and bold)
xfonts-intl-arabic - International fonts for X -- Arabic

My guess is you'll need
language-support-fonts-ar
ttf-arabeyes
ttf-kacst
ttf-sil-scheherazade
emacs-intl-fonts
xfonts-intl-arabic

But I haven't ever needed to install arabic font support, so I couldn't say from experience, sorry.

---

### Post by yghannam7388 on 2009-12-11
hey guys,

QuranExplorer uses the PDMS_IslamicFont which is an Embedded OpenType font. Embedded OpenType is proprietary and belongs to Microsoft and so it won't be easy to get it working with Firefox on Ubuntu.  

I got it to work by downloading the PDMS TrueType fonts then installing them in Ubuntu. To get the fonts, click on the "font" button at the bottom of the QuranExplorer window. This downloads a .exe file. Extract the file using Ubuntu's archive manager. Then install the fonts; I used the following tutorial: [http://www.wikihow.com/Install-True-Type-Fonts-on-Ubuntu](http://www.wikihow.com/Install-True-Type-Fonts-on-Ubuntu)

I hope this works for you too.

---

### Post by sani.supahan on 2011-03-03
Salam,

for Ubuntu users:

1) simply download the PDMS font [http://www.quranexplorer.com/Quran/Downloads/PDMS_FontsSetup_b2.exe](http://www.quranexplorer.com/Quran/Downloads/PDMS_FontsSetup_b2.exe) on a Windows machine and extract it's contents

2) save onto a flash drive or email to your own alternate email, so you can easily access the PDMS .TTF files on our Ubuntu machine

3) access /usr/share/fonts/truetype via root nautilus by typing >> gksu nautilus ; then enter root password

4) copy and paste .TTF files into /usr/share/fonts/truetype

Viola!!

---

