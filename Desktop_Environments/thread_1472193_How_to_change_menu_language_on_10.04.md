---
title: "How to change menu language on 10.04?"
date: 2010-05-04
forum: Desktop Environments
---

### Post by Xamindar on 2010-05-04
I did the upgrade to 10.04 and now all my menus are in Japanese (wifes logon is in japanese but mine was english before). Was language support broken in 10.04? As far as I can tell my language is still set to English, even at the login screen. But everything is still Japanese. Can anyone confirm this problem?

---

### Post by AlexDudko on 2010-05-04
Yes, I can confirm the same problem with Russian language. And there's no way to change it back.

---

### Post by angelv on 2010-05-14
Hi,

I had a similar problem. My wife also uses this laptop. We both want a Spanish keyboard, but she wants the menus in Spanish while I prefer them in English. For some reason, after updating to 10.04 my menus were also in Spanish. 

In the language support tool I had the following languages (in that order) English (United Kingdom), Spanish, English, but then I always got the menus in Spanish. Moved away Spanish below English and all is fine now. Perhaps the support for UK English is broken?

I don't know if this could solve your problem...

Cheers,
Ángel de Vicente

---

### Post by AlexDudko on 2010-05-14
A workaround to change menu language is to manually edit **/etc/default/locale**.
For instance, to change everything to English (US) it should look like this:
> LANG="en_US.utf8"
LANGUAGE="en_US:en"

---

### Post by ghormax on 2010-05-30
I also have a similar problem. I am using English Ubuntu and cannot switch the menus to any other language as in previous versions. This is a real pity because I think this was a great advantage of Ubuntu.

---

### Post by grooverider on 2010-06-15
works for me. i have a fresh install of 10.4. I change the settings in 'system-->administration-->language support' to install extra language, then you need to get the language you want to be in the 'not grayed out' zone, so in the pic below only english is active [IMG]http://img405.imageshack.us/img405/2535/screenshotto.png[/IMG]
after setting the language you want you need to log out and select during login at the bottom bar what language to choose, hope it helps :)

---

### Post by spamless on 2010-06-17
> **AlexDudko said:**
> A workaround to change menu language is to manually edit **/etc/default/locale**.
For instance, to change everything to English (US) it should look like this:

But I want the system language in German, yet my own login's menus and foldernames in English.

---

