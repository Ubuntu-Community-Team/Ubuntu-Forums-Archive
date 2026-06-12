---
title: "Spell checking problem"
date: 2012-01-13
forum: Desktop Environments
---

### Post by UbuBegUsr on 2012-01-13
Hello, I've 2 languages (Arabic and English). Spell checking in English puts red line under every word I write in a textbox but it works currently in Arabic. The problem's exist in Firefox only.
There's an add-on in Languages I don't know how was it installed. It's English (South Africa) Language Pack 9.0.1. Is it the reason?
[SIZE=1]Note: My Ubuntu's updated.[/SIZE]

---

### Post by claracc on 2012-01-14
Do you need english (south african) language pack? you can inactivate it or uninstall in firefox if you are not using.

Also, if you untick in edit--> preferences--> advanced---> general, navigate, spell check while writing you can get rid of red line.

You can also try to install the quick locale switcher addon [https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/](https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/) to work with the two languages

---

### Post by UbuBegUsr on 2012-01-14
> **claracc said:**
> Do you need english (south african) language pack? you can inactivate it or uninstall in firefox if you are not using.

Also, if you untick in edit--> preferences--> advanced---> general, navigate, spell check while writing you can get rid of red line.

You can also try to install the quick locale switcher addon [https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/](https://addons.mozilla.org/en-US/firefox/addon/quick-locale-switcher/) to work with the two languages
Hello, I disabled English (sou...) add-on but the problem's still exist. I can untick spell checking but can developers fix the problem in spell checking?

---

### Post by spacecheck on 2012-01-14
> **UbuBegUsr said:**
> Hello, I've 2 languages (Arabic and English). Spell checking in English puts red line under every word I write in a textbox but it works currently in Arabic. The problem's exist in Firefox only.
There's an add-on in Languages I don't know how was it installed. It's English (South Africa) Language Pack 9.0.1. Is it the reason?
[SIZE=1]Note: My Ubuntu's updated.[/SIZE]
In Firefox you can right click the red underlined word, then select "Languages". If only English is listed, you could select "Add dictionaries" to locate one for Arabic. The when you write Arabic, it will underline misspelled words in that language. When you write in English, you will have to right click and select "languages" to switch from "Arabic" to "English", etc.

Is that what you mean??

Good luck!

---

### Post by UbuBegUsr on 2012-01-15
> **spacecheck said:**
> In Firefox you can right click the red underlined word, then select "Languages". If only English is listed, you could select "Add dictionaries" to locate one for Arabic. The when you write Arabic, it will underline misspelled words in that language. When you write in English, you will have to right click and select "languages" to switch from "Arabic" to "English", etc.
Is that what you mean??
Good luck!
Hello spell checking's selected in Arabic so when I write any word in English, it puts a red line but when I select English, it doesn't put a red line under Arabic!!!

---

### Post by spacecheck on 2012-01-15
Do you have both Arabic and English dictionaries installed?

---

### Post by UbuBegUsr on 2012-01-15
> **spacecheck said:**
> Do you have both Arabic and English dictionaries installed?
Hello, yes, I've them both.

---

### Post by lovinglinux on 2012-01-20
Use [Dictionary Switcher](https://addons.mozilla.org/en-US/firefox/addon/dictionary-switcher/). It can detect the page language and switch to the corresponding spelling dictionary automatically.

---

### Post by UbuBegUsr on 2012-01-22
> **lovinglinux said:**
> Use [Dictionary Switcher]("https://addons.mozilla.org/en-US/firefox/addon/dictionary-switcher/"). It can detect the page language and switch to the corresponding spelling dictionary automatically.
This's not my problem. My problem's if I wanted to change the language from Arabic to English in the same  website, I'll have to change the dictionary so as not to see a red line under every English word. The add-one won't do this.

---

### Post by Krytarik on 2012-01-22
> **UbuBegUsr said:**
> My problem's if I wanted to change the language from Arabic to English in the same  website, I'll have to change the dictionary so as not to see a red line under every English word.
Yeah, this is the expected behaviour; you can't have multiple languages enabled for spell checking at the same time, as also indicated by the radio check marks in the respective menu. ;-)

Regards.

---

### Post by UbuBegUsr on 2012-01-23
> **Krytarik said:**
> Yeah, this is the expected behaviour; you can't have multiple languages enabled for spell checking at the same time, as also indicated by the radio check marks in the respective menu. ;-)
Regards.
Hello, in this case, I accept it. This's the last problem and I think I understand it now. :D When I write in English using the **Arabic dictionary**, I see a red line under every English word. When I write in Arabic using the **English dictionary** I don't see a red line under every Arabic word.
So the problem's the Arabic dictionary considers every unArabic word and a wrong Arabic word _a spelling mistake in an Arabic word_ but the English dictionary only considers every wrong English word _an English word with spelling mistake_. The English dictionary don't do the same with other languages.
Will they fix the problem in the Arabic dictionary or maybe other dictionaries if it's exist in a next update?

---

### Post by Krytarik on 2012-01-23
Ok, I've definitely got now what you mean :P , and apparently this behavior also applies to all other non-Latin scripts, I've just tested that with a lot of them. And apparently it doesn't matter what Latin-based language you've selected for spell checking, I've tested that with both English and German.

> **UbuBegUsr said:**
> Will they fix the problem in the Arabic  dictionary or maybe other dictionaries if it's exist in a next  update?
In fact, this is an issue with the other dictionaries, for Latin-based scripts, or the spell checking system in general, I suppose; the Arabic spell checking is working as expected, just fine, that is. :D

---

### Post by UbuBegUsr on 2012-01-23
> **Krytarik said:**
> Ok, I've definitely got now what you mean :P , and apparently this behavior also applies to *all* non-Latin scripts, I've just tested that with a lot of them. And apparently it doesn't matter what Latin-based language you've selected for spell checking, I've tested that with both English and German.


In fact, this is an issue with the other dictionaries, for Latin-based scripts, or the spell checking system in general, I suppose; the Arabic spell checking is working as expected, just fine, that is. :D
I hope they fix it.
Problem: [COLOR=Lime]Solved[/COLOR].

---

