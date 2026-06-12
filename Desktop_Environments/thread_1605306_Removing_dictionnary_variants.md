---
title: "Removing dictionnary variants"
date: 2010-10-25
forum: Desktop Environments
---

### Post by dargaud on 2010-10-25
Hello all,
I write in several language and Ubuntu has indeed too much coverage for those languages. I would like to remove the dictionary variants such as English (Australia), French (Belgium), etc, to leave only English (United States of America), French... because every 2 minutes I have to slog through this long list of 15 variants I'll never use.

I tried 
```
sudo aptitude remove myspell-en-au myspell-en-gb myspell-en-za
```
but it wants to remove language-support-writing-en.

Thanks

---

### Post by dargaud on 2010-11-09
Nobody ? That's probably a simple config file somewhere... KDE specific maybe ?

---

### Post by dargaud on 2012-12-27
OK, still keeping this thread alive as I still find this issue annoying. I still cannot find in which files the sub-localizations as kept. For instance let's take belgian:
```
$ aptitude search $(sudo apt-cache search belgi | cut -d" " -f1)
p   beid-mozilla-plugin                                    - beID mozilla plugin                                             
p   beid-mozilla-plugin:i386                               - beID mozilla plugin
...
```
There's not a single installed package.
Same if I do:
```
$ locate fr-be
/usr/share/virtualbox/rdesktop-vrdp-keymaps/fr-be

```
Is this one for instance part of a standard fr spell checker and impossible to remove ?

---

### Post by zombifier25 on 2012-12-27
I use BleachBit, and one of its jobs is to get rid of unused language files. Give it a try.

---

