---
title: "Spell-checker bug"
date: 2009-11-20
forum: Desktop Environments
---

### Post by _C_ on 2009-11-20
I've found this bug: [https://bugs.launchpad.net/ubuntu/+source/enchant/+bug/254223](https://bugs.launchpad.net/ubuntu/+source/enchant/+bug/254223) and it's really annoying me.  Across all applications, from Pidgin and Empathy to Tomboy, the spell-checker just does not work.  It underlines all sorts of words as being mis-spellings (see the bug link for images) when they are clearly not mis-spelled.

It's been open for a year, and nobody from Ubuntu seems to care.  I would actually prefer to *not have a spell-checker **at all***, rather than have one that underlines every 3rd or 5th words with red!

Who can point me to a way to bring this to the attention of the right people?  I'm not looking for a workaround, I'm looking for a fix, because I don't want to help others to install a desktop environment that, out-of-the-box, requires fiddling to get simple funcitonality right.

---

### Post by emigrant on 2009-11-20
is there something wrong with your language settings?

---

### Post by JBAlaska on 2009-11-20
You might try changing dictionary's as my spell-checker has always worked fine and if it effected everyone there would be a lot more complaining.

---

### Post by _C_ on 2009-11-20
> **emigrant said:**
> is there something wrong with your language settings?

I haven't changed a thing related to language settings.  I put my location as South Africa when it asked during setup, and I assume that it chose the correct language settings for me.  If it didn't, well, that's another bug, and one which would appear to affect the entire country.

---

### Post by JBAlaska on 2009-11-20
Ubuntu has virtual packages called language-support-xx , where xx is a country code. language-support-en installs both the British and the American dictionaries for the main spell-checker engines used by applications in Linux: aspell and myspell.

aspell is the most used, both by GNOME and KDE, and the specific package aspell-en installs both British and US dictionaries. It defaults to the language of your system.
You can either change for each GNOME and KDE app the dictionary you want to use (boring), or change your locales preference, in a local or global way.
Local: In gdm, enter your username, and choose your language.
Global: If you want all users in your system to use the same language, thus use the same dictionary, run:
```
sudo dpkg-reconfigure locales
```
myspell is the spellchecker which Openoffice.org uses (if not the only one, one of the few application which do) . The English packages are separated into myspell-en-gb and myspell-en-us. So you can either remove the myspell-en-us package, or configure it inside open-office.

If Open-office spell-checker works right, then aspell may be the culprit, Try changing your local to the us (To use the us dictionary) or if that does not work try changing to Britain..etc.

---

### Post by Arup on 2009-11-20
I face the same issue with fresh Karmic x64 install. All legitimate words in Empathy are being outlined as wrong. I select US English by default.

---

### Post by _C_ on 2009-11-21
Thanks for all the replies here, and I'm sure that setting my dictionary to en-US or en-GB will help with this problem.  However, **I don't want to work around this problem**.  I regard this is a quality issue with Ubuntu.  I would rather that they fix it: if that means selecting "en-US" or "en-GB" for all South Africans *by default*, then that is what they should do.  It is unacceptable for a default install to display this behaviour, especially if the fix is as trivial as changing the default dictionary setting.

_Can anyone tell me how to bring this bug to the attention of right person?_  This bug has existed in Ubuntu since version **8.04**.  And it is *still not fixed*.  This affects (and has affected) users from day one, in multiple different applications.  It boggles my mind that something like this is not on the 100-papercuts list: how can I bump up its priority?

---

