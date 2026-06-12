---
title: "Help, Language support dialog close itself now."
date: 2009-08-08
forum: Desktop Environments
---

### Post by rexebin on 2009-08-08
What I did was trying to get ubuntu to support Chinese better by doing the following:

1. sudo cp /var/lib/locales/supported.d/local /var/lib/locales/supported.d/local.old (backup)
2. sudo cp /usr/share/i18n/SUPPORTED /var/lib/locales/supported.d/local
3. sudo dpkg-reconfigure locales
4. sudo locale-gen zh_CN.UTF-8 

After doing so, my problem was not solved of cause. More importantly the Language Support from System-adminstration is broken by the above step, the dialogue of Language Support now close itself after checking  available language support finished.

Then I tried to revert the above step buy copying back the backup local and reconfigure locales and set default to en_US.UTF-8. However, the Language Support is still not working. Help! here is that I did to revert:
1. sudo cp /var/lib/locales/supported.d/local.old /var/lib/locales/supported.d/local
2. sudo dpkg-reconfigure locales
3. sudo locale-gen en_US.UTF-8

I thought I restored what I have done, but it's not working, why? 

I am very new to Linux, impressed to the usability of Ubuntu, amazed by Synaptic package manager, however, I also found the system is easy to be damned and it's hard to restore, it's probably because I am too new to it. wish I could get better.

Help please.

I managed to run Language Support in Terminal, here you go:
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:839: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 34, in <module>
    options=options)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 171, in __init__
    self.updateUserDefaultCombo()
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 58, in wrapper
    res = f(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 858, in updateUserDefaultCombo
    COMBO_LANGUAGE,self._localeinfo.translate(locale),
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 136, in translate
    (lang_name, country_name) = self.translate_locale(locale)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 126, in translate_locale
    lang_name = self.translate_language(lang)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 110, in translate_language
    lang_name = gettext.dgettext('iso_639', self._lang[lang])
KeyError: 'iw'

Any hint?

---

