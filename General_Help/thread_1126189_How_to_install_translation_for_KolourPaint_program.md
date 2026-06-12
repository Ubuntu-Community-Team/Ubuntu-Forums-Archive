---
title: "How to install translation for KolourPaint program?"
date: 2009-04-15
forum: General Help
---

### Post by abcuser on 2009-04-15
Hi,
I have installed KolourPaint painting program using Application | Add/Remove in Ubuntu 8.10.

But I see no translation for my language. Translation exists in Launchpad:
[https://translations.launchpad.net/ubuntu/intrepid/+source/kdegraphics/+pots/kolourpaint](https://translations.launchpad.net/ubuntu/intrepid/+source/kdegraphics/+pots/kolourpaint)

How to install my language support to use KolourPaint in my local language?
Regards

---

### Post by abcuser on 2009-04-16
PROBLEM SOLVED!

I have found out solution and it is working fine. Bellow are detailed instructions for people having the same problem:

1. To have kolourpaint in my language (e.g. Slovenian) I have to install "Slovenian KDE" package. Find out all Slovenian & KDE packages:
```
apt-cache search slovenian | grep "KDE" | grep "Slovenian"
```

Output of this command is:
kde-l10n-sl - Slovenian (sl) localisation files for KDE4
kde-i18n-sl - Slovenian (sl) internationalized (i18n) files for KDevelop and KDEWebDev
language-pack-kde-sl - KDE translation updates for language Slovenian
language-pack-kde-sl-base - KDE translations for language Slovenian

2. From output from previous command I see I have to install kde-l10n-sl, language-pack-kde-sl and language-pack-kde-sl-base packages (package kde-i18n-sl is not related to KolourPaint so no need of installing). But I now know if installing kde-l10n-sl package also other two are installed because of dependencies. So installing kde-l10n-sl package:
```
sudo apt-get -y install kde-l10n-sl
```

3. Start kolourpaint in my language
Login to Ubuntu with Slovenian locale. KolourPaint is started in Slovenian.
```
kolorpaint
```

4. I see KolourPaint is translated to Slovenian language, but not all strings are translated. So I opened Launchpad and check untranslated strings and I see there are not all strings translated for Ubuntu 8.10. Then I have checked to see if there is KolourPaint for Ubuntu Jaunty translated and I see it is. So I have downloaded the MO file from Launchpad from URL (you have to be registered and logged in to Lauchpad): [https://translations.launchpad.net/ubuntu/jaunty/+source/kdegraphics/+pots/kolourpaint/sl/+export](https://translations.launchpad.net/ubuntu/jaunty/+source/kdegraphics/+pots/kolourpaint/sl/+export)

If you are not registered to Launchpad, you can download Slovenian version directly from:
[http://launchpadlibrarian.net/25530430/sl_LC_MESSAGES_kolourpaint.mo](http://launchpadlibrarian.net/25530430/sl_LC_MESSAGES_kolourpaint.mo)

Default downloaded file name saved to disk is: sl_LC_MESSAGES_kolourpaint.mo

5. Find out where is original location of mo file for KolourPaint
```
sudo find / -name kolourpaint.mo
```

Output of command is: /usr/share/locale-langpack/sl/LC_MESSAGES/kolourpaint.mo

6. Overwrite downloaded file with original file in /usr/ subdir:
```
sudo mv sl_LC_MESSAGES_kolourpaint.mo /usr/share/locale-langpack/sl/LC_MESSAGES/kolourpaint.mo
```

7. Start KolourPaint again:
Now all strings in KolourPaint are translated in Slovenian. Excellent!
Regards

---

