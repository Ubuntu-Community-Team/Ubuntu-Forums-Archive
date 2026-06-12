---
title: "What is wrong with Python?"
date: 2009-06-12
forum: General Help
---

### Post by stoned_again on 2009-06-12
For example... when i try to run the language selector...

```
wolvz@wolvz-laptop:~$ /usr/bin/gnome-language-selector
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:837: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 34, in <module>
    options=options)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 171, in __init__
    self.updateUserDefaultCombo()
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 58, in wrapper
    res = f(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 850, in updateUserDefaultCombo
    defaultLangName = self._localeinfo.translate(defaultLangCode)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 148, in translate
    return self.translate_language(locale)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 110, in translate_language
    lang_name = gettext.dgettext('iso_639', self._lang[lang])
KeyError: 'C'
wolvz@wolvz-laptop:~$ 
```

and, another example.. when i try to run [djl](http://en.djl-linux.org/)...

```
wolvz@wolvz-laptop:~/Desktop/djl$ ./djl.sh
This is the first djl launch
Traceback (most recent call last):
  File "djl.py", line 486, in <module>
    main()
  File "djl.py", line 401, in __init__
    self.verif_demarrage()
  File "djl.py", line 188, in verif_demarrage
    import configuration
  File "/home/wolvz/Desktop/djl/djl/configuration.py", line 28, in <module>
    from variables import variables
  File "/home/wolvz/Desktop/djl/djl/variables.py", line 29, in <module>
    class variables:
  File "/home/wolvz/Desktop/djl/djl/variables.py", line 59, in variables
    liste_canaux = [""]*len(config.config(info=16)) #Va chercher la liste des canaux suivant la configuration)
  File "/home/wolvz/Desktop/djl/djl/config.py", line 210, in config
    loc = locale.getdefaultlocale()[0].split("_")[0]
AttributeError: 'NoneType' object has no attribute 'split'
wolvz@wolvz-laptop:~/Desktop/djl$
```

Help me please...
i'm using ubuntu 9.04.

---

### Post by Mighty_Joe on 2009-06-12
I'm no Python guru, but it looks like your localization is screwed up, not Python itself.  If you look at the root of the tracebacks:

```
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 110, in translate_language
    lang_name = gettext.dgettext('iso_639', self._lang[lang])

```

```
  File "/home/wolvz/Desktop/djl/djl/config.py", line 210, in config
    loc = locale.getdefaultlocale()[0].split("_")[0]

```

both appear to be loading some sort of language customization.  When you installed Ubuntu, what language did you select?  Did you do a clean install or an upgrade?  Did you change languages after you installed?

---

### Post by sedawk on 2009-06-12
What is the content of your "LANG" variable?
```

echo $LANG

```

Here LANG is "en_US.UTF-8"

Please check your environment (run "env" in terminal") for
any language specific variables of the same style.
Are there any variables set in your environment where
the variable's name starts with LC_?
(something like LC_ALL set to "C"?).

---

### Post by stoned_again on 2009-06-12
> **Mighty_Joe said:**
> 

When you installed Ubuntu, what language did you select?  Did you do a clean install or an upgrade?  Did you change languages after you installed?

I didn't select any language, and i think that's the problem. I don't remember the option i chose in the installation, but i remember i didn't specified a language. But my current language is clearly english. I did a clean install. No.

> **sedawk said:**
> What is the content of your "LANG" variable?
```

echo $LANG

```

Here LANG is "en_US.UTF-8"

Please check your environment (run "env" in terminal") for
any language specific variables of the same style.
Are there any variables set in your environment where
the variable's name starts with LC_?
(something like LC_ALL set to "C"?).

here:

```
wolvz@wolvz-laptop:~$ echo $LANG
C

```

```
wolvz@wolvz-laptop:~$ env
(...)
LANG=C
(...)
GDM_LANG=C
(...)

```

these are the options set to "C".
the option LC_something doesn't appear.

Sorry for the bad english guys. And thanks for the help!

---

### Post by jeromedavies on 2009-06-12
OT: is "Stoned_again" a reference to th e Faublous Furry Freak Brothers?

---

### Post by stoned_again on 2009-06-12
> **jeromedavies said:**
> OT: is "Stoned_again" a reference to th e Faublous Furry Freak Brothers?

No, lol. My brother went to Holland years ago, he bought a t-shirt that said "i'm stoned again" (or something like that). I found it funny, and adapted the t-shirt's sentence to a nickname.

--

So... anyone knows the solution for my problem? What if i add the option LANG=en_US.UTF-8 to the /etc/environment file?

---

### Post by blackxored on 2009-06-12
You're getting KeyError when accessing the language information in GtkLanguageselector or something. As you may guess KeyError is an exception raised when It doesn't find a given key on a dictionary-like instance. And when you pointed that LANG=C in your system, that's of course the problem. Open ~/.bashrc. 
Go to end and put:
> 
export LANG=en_US.UTF-8


And then:
```

source ~/.bashrc

```

How did 'C' got into your LANG var is harder to say ;)
Check also your LC_* vars.

If that seems to work well then put it in a system-wide basis. 

Hope it helps.

---

### Post by stoned_again on 2009-06-12
I did what you said (changed the GDM_LANG too),
```
LANG=en_US.UTF-8
GDM_LANG=en_US.UTF-8

```

but now, when i run the language selector:

```
wolvz@wolvz-laptop:~$ /usr/bin/gnome-language-selector

[B](process:3963): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.[/B]
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:837: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 34, in <module>
    options=options)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 171, in __init__
    self.updateUserDefaultCombo()
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 58, in wrapper
    res = f(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 850, in updateUserDefaultCombo
    defaultLangName = self._localeinfo.translate(defaultLangCode)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 148, in translate
    return self.translate_language(locale)
  File "/usr/lib/python2.6/dist-packages/LanguageSelector/LocaleInfo.py", line 110, in translate_language
    lang_name = gettext.dgettext('iso_639', self._lang[lang])
KeyError: 'C'

```

I don't find any LC_* vars when i type _env_ in the terminal.

---

### Post by blackxored on 2009-06-12
I didn't asked you to touch GDM_LANG but It doesn't hurts either. Please try the following:
```

sudo aptitude install language-support-en language-pack-en language-pack-gnome-en
update-locale LANG=en_US.UTF-8 LANGUAGE

```

---

### Post by stoned_again on 2009-06-12
Removed the line **export GDM_LANG=en_US.UTF-8** from ~/.bashrc.

Thank you, it worked. I've already installed djl, which i couldn't install before.

When i run language selector, a few warning show up, but i guess it is fine, because the Language Support window now appears...
Anyway, the warnings:

```
wolvz@wolvz-laptop:~$ /usr/bin/gnome-language-selector
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:837: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]
/usr/lib/python2.6/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py:804: GtkWarning: gtk_cell_view_set_cell_data: assertion `cell_view->priv->displayed_row != NULL' failed
  cell = combo.get_child().get_cell_renderers()[0]

```

Also... during the installation of language-support-en, language-pack-en and language-pack-gnome-en this warning occurred several times:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

I've opened the terminal and typed env but LC_* vars are still not listed. Should i set them? How can i do it?
Using this maybe -> update-locale LANG=en_US.UTF-8 LANGUAGE LC_ALL ?

---

### Post by blackxored on 2009-06-12
You're of course welcome. :D

```

[B]sudoedit /etc/default/locale
[/B]export LANG="en_US.UTF8"

```
That should perform what the perl scripts are complaining about. 

BTW, I haven't set LC either since I'm using just english and works fine.

---

### Post by stoned_again on 2009-06-12
Nope. I added that line to the locale file but the warnings persist. But the language selector is working fine i think. Do you know another possible solution? If not, don't mind! You have already solved the main problem. :P

I really appreciate your help! Thanks again!

---

