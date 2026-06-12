---
title: "After Upgrading Today...."
date: 2006-06-16
forum: Desktop Environments
---

### Post by 89c51 on 2006-06-16
... all the gtk menus in the place where the shortcut appears the have additional text ie "keyboard label | Ctrl+A"

look at the screen shot

how can i fix this????

[http://img216.imageshack.us/img216/3639/screenshot1ah.png](http://img216.imageshack.us/img216/3639/screenshot1ah.png)

---

### Post by kreso on 2006-06-18
yeah, I've got the same problem :(

---

### Post by Ramses de Norre on 2006-06-18
Strange, it doesn't occur here, did you try changing themes?

---

### Post by valmy on 2006-06-19
No, it's not related to theme used as it happens in all themes.

---

### Post by forgreatjustice on 2006-06-19
okay, i have fixed it....

goto: system > administration > language support

and set your default language to something different than austrailian english

(like US or GB english)

cya

---

### Post by simonn on 2006-06-19
But... I'm Australian so I do not consider that a fix.

...and I thought Ubuntu was all about international group hugs!

grrr.

---

### Post by tristan on 2006-06-19
I notice that this morning's round of updates (acpi stuff only) did NOT fix this highly annoying and visible bug.

---

### Post by kreso on 2006-06-19
Thanks man! but, why is ubuntu's default language Australian English and why on earth does that cause the error?

---

### Post by az on 2006-06-19
[QUOTE=simonn]But... I'm Australian so I do not consider that a fix.

...and I thought Ubuntu was all about international group hugs!

grrr.[/QUOTE]
Please file a bug.

---

### Post by simonn on 2006-06-19
Thought I would investigate it first...

If anyone want to know...

In language-pack-gnome-en_6.06+20060614 translation strings for "keyboard label | ...." were added when they should not have been.

If you want to solve this whilst remaining a good aussie, downgrade to (UNTESTED - I DO NOT HAVE ACCESS TO A GNOME SESSION WHERE I AM NOW!):

[ftp://ftp.iinet.com.au/pub/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_6.06+20060529_all.deb](ftp://ftp.iinet.com.au/pub/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_6.06+20060529_all.deb)

---

### Post by simonn on 2006-06-19
Bug #50412

---

### Post by simonn on 2006-06-19
[QUOTE=kreso]Thanks man! but, why is ubuntu's default language Australian English[/quote] 

I do not think it is.

This may not be unique to the en_AU locale.

> and why on earth does that cause the error?

In a nut shell:

The way translation works on linux is like so, in theory anyway - being sadly monolinguistic I would be a crap translator.

Developers write an application in a language/locale, usually eng_US. They mark any text strings which may need translation and instead of displaying the message directly they call gettext with the base message. Gettext will look up the message in translation files (.mo file - have a look in /usr/share/locale-langpack/[locale]/LC_MESSAGES/).

e.g. if using glib instead of using:

g_printf( "Number One" );

use:

g_printf( _( "Number One" ) );

The _() macro, marks the text for translation and also calls gettext to do the translation at runtime. 

By marking the text, translators can run gettext over source code and this will create a table of strings to be translated, a .po file, which is compiled into a .mo file.

At runtime, gettext will look for a match for the string in the .mo file for your locale and display that instead. If no message is found in the translation file or there is no translation file, it will display the default, in the case above "Number One".

In the Italian translation file, for example, "Number One" would be substituted with "Numero Uno".

What I suspect is happening here is that a translator forgot to not translate the "keyboard label|..." strings in gtk20.po.

---

### Post by jgcamp99 on 2006-06-20
Australian English ?, does it have an aussie accent ? ;)

---

### Post by thepizzaking on 2006-06-23
You can get un updated package, just add this source:
deb [http://people.ubuntu.com/~pitti/langpacks/daily/dapper-updates/](http://people.ubuntu.com/~pitti/langpacks/daily/dapper-updates/) ./
it seems to have fixed it here :)

---

