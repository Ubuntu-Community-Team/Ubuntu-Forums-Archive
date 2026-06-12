---
title: "Serious problems with Dapper 6.06 after update yesterday"
date: 2006-08-02
forum: Desktop Environments
---

### Post by fantan on 2006-08-02
Hi Everybody,

I'd like just to inform, that after automatic update yesterday, my Ubuntu Dapper 6.06 system became crazy.
I'm a Hungarian, I use Hungarian language, Hungarian keyboard, etc. After installation I woked a lot to set up my system well, as I like it.  
But yesterday, after I did the automatic update, my Gnome desktop became English, that is the right-click pull-down menu on the Desktop changed from Hungarian to English (it is interesting, but the main menu left Hungarian);
What's more, also the menu items in Evolution became English; the screen-refresh in Evolution doesn't work (I mean for example, when I delete an e-mail or more, the counter of not-readed items not decreases just in case if I move the mouse cursor over boxes in the Inbox folder).
I've checked the environment variables, but they are set to Hungarian:
LANG=hu_HU.UTF-8
LANGUAGE=hu_HU.UTF-8
LC_ALL=hu_HU.UTF-8
LC_CTYPE=hu_HU.UTF-8
LC_COLLATE=hu_HU.UTF-8
LC_TIME=hu_HU.UTF-8
LC_NUMERIC=hu_HU.UTF-8
LC_MONETARY=hu_HU.UTF-8
LC_MESSAGES=hu_HU.UTF-8
LC_PAPER=hu_HU.UTF-8
LC_NAME=hu_HU.UTF-8
LC_ADDRESS=hu_HU.UTF-8
LC_TELEPHONE=hu_HU.UTF-8
LC_MEASUREMENT=hu_HU.UTF-8
LC_IDENTIFICATION=hu_HU.UTF-8
I've checked the Language Selector and the Language Support too, but they are set up to Hungarian as well.

To tell you the truth, in my sources.list I've enabled the "deb [http://people.ubuntu.com/~pitti/langpacks/daily/dapper-updates](http://people.ubuntu.com/~pitti/langpacks/daily/dapper-updates) ./" repository, and it is possible that there is some problem with language packs too. Just the problem is that I don't know, where to search the solutions, how to downgrade those packs if the solution is the downgrade at all.

Can anybody help me, what to do with these?
Both the change of the language and the screen refresh problem in Evolution are very annoying but the language change is the most annoying.

fantan

---

### Post by Blairboy on 2006-08-02
Run "apt-cache search hungarian" and make sure that it didn't accidentally remove them.  If everything's set to hungarian but you don't have the packages, it's going to cause problems.

---

### Post by fantan on 2006-08-02
Hi,

When running the "apt-cache search hungarian" command I get in the terminal the following messages:
albert@ubuntu:~$ apt-cache search hungarian
aspell-hu - Hungarian dictionary for aspell
dict-freedict-eng-hun - Dict package for English-Hungarian Freedict dictionary
dict-freedict-hun-eng - Dict package for Hungarian-English Freedict dictionary
easytag - viewing, editing and writing ID3 tags
enca - Extremely Naive Charset Analyser - binaries
enigmail-locale-hu - Hungarian language package for Enigmail
gcompris-sound-hu - Hungarian sound files for GCompris
hunglish - A consistent English-Hungarian keyboard layout
hunspell - spell checker and morphological analyzer (program)
ihungarian - The Hungarian dictionary for ispell
imp3 - Web Based Mail Program
koffice-i18n-hu - Hungarian (hu) translations for KOffice
ldap-account-manager - webfrontend for managing accounts in an LDAP directory
libhunspell-dev - spell checker and morphological analyzer (static library)
manpages-hu - Hungarian manpages
mozilla-locale-hu - Hungarian menus for Mozilla
sylpheed-claws-gtk2-i18n - Locale data for Sylpheed Claws (i18n support)
sylpheed-claws-i18n - Locale data for Sylpheed Claws (i18n support)
sylpheed-gtk1-i18n - Locale data for Sylpheed (i18n support)
sylpheed-i18n - Locale data for Sylpheed (i18n support)
kde-i18n-hu - Hungarian (hu) internationalized (i18n) files for KDE
language-support-hu - metapackage for Hungarian language support
mozilla-firefox-locale-hu-hu - Mozilla Firefox Hungarian language/region package
myspell-hu - The Hungarian dictionary for myspell
openoffice.org-help-hu - Hungarian help for OpenOffice.org
openoffice.org-hyphenation-hu - Hungarian hyphenation patterns for OpenOffice.org
openoffice.org-l10n-hu - Hungarian language package for OpenOffice.org
thunderbird-locale-hu - Thunderbird Hungarian language/region package
language-pack-gnome-hu-base - GNOME translations for language Hungarian
language-pack-hu-base - translations for language Hungarian
language-pack-kde-hu-base - KDE translations for language Hungarian
language-pack-gnome-hu - GNOME translation updates for language Hungarian
language-pack-hu - translation updates for language Hungarian
language-pack-kde-hu - KDE translation updates for language Hungarian
albert@ubuntu:~$ 

And what is now?
Ho to go forward?
What can I do away?

fantan

---

### Post by thepizzaking on 2006-08-04
I'm having the same problem, except with British English instead of Hungarian.
After the update, all of my 'U's are gone, and my 'S's all turned to 'Z's :cry:

---

