---
title: "Default British Spell Checker Dictionary?"
date: 2008-12-16
forum: General Help
---

### Post by RKBA on 2008-12-16
Greetings,

I'm new here and not sure where to post this, so please feel free to tell me where to go :p or to move this question.

Apparently, a British spell checker dictionary was installed as part of the default Ubuntu 8.10 installation even though I was *very* careful to select American English as the default language during installation (I've installed Ubuntu at least twice and was aware of the problem the last time I installed it, so was very careful about language selection). I am *assuming* there is a system wide dictionary involved here, since the British spelling is foisted upon me not only in Firefox but in other system applications with spell checkers such as gedit, although OpenOffice is unaffected and allows me to use words like "honor" without trying to change it to "honour", etc. I've been "adding" the American English spelling to the dictionary, but surely there must be a way to replace the whole thing in one fell swoop, I would hope. 

Does anyone know where the dictionary I need to replace is located, and where I could find a suitable replacement, or am I totally off base here?

Thank you,

Ron

---

### Post by clconway on 2009-01-30
I had the same question. You should have a U.S. English dictionary installed, which you can select by right-clicking in a text box and choosing "Languages -> English / United States" (you should also have a choice of British and Australian).

---

### Post by PriceChild on 2009-01-30
System > Administration > Language Support

---

### Post by clconway on 2009-01-30
> **PriceChild said:**
> System > Administration > Language Support
This is not a solution to the stated problem. I have "English (United States)" selected in "System > Administration > Language Support"---I selected U.S. English as the default at installation---but the British English dictionary is used by default in Firefox. I'm not sure if it's a packaging bug or a problem in Firefox. See Launchpad [Bug #320266]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/320266")

---

### Post by antony_css on 2009-02-10
In openoffice, "English(US)" can be set as the default language.
I discovered it when I tried to turn on the automatic spellcheck function:

*Tools > Options > Language settings > Languages*
You will see the empty field *Western*, and you can select the default language yourself.

---

### Post by bdentremont on 2009-04-06
From gEdit menus try "Tools/Set Language..." and select "English (United States)" rather than "English".

Works on Ubuntu 8.10, gedit 2.24.2

I am not sure why this is so hard to notice, but I wouldn't be at this forum myself if I had seen it the first time through.

---

### Post by ssully on 2009-12-03
> **bdentremont said:**
> From gEdit menus try "Tools/Set Language..." and select "English (United States)" rather than "English".

Works on Ubuntu 8.10, gedit 2.24.2


Yup, that's the way to do it.  Seems like it might be a good idea to set English (United States) as conditional default at install.  "Tools/Set Language" is an easy fix, but not one that the average user should have to make.

---

### Post by freetolio on 2010-01-26
> **clconway said:**
> I had the same question. You should have a U.S. English dictionary installed, which you can select by right-clicking in a text box and choosing "Languages -> English / United States" (you should also have a choice of British and Australian).

Thanks, this fixes it in Firefox for me.:KS

---

### Post by audiomick on 2010-01-26
> **ssully said:**
> Seems like it might be a good idea to set English (United States) as conditional default at install.  "Tools/Set Language" is an easy fix, but not one that the average user should have to make.

If that means that those of us who want British spelling have to change, don't even think about it! Being able to choose in a way that is really system wide, sure, but don't give me American spelling by default.:p

---

### Post by clconway on 2010-01-26
> **audiomick said:**
> If that means that those of us who want British spelling have to change, don't even think about it! Being able to choose in a way that is really system wide, sure, but don't give me American spelling by default.:p

Ubuntu does have a system-wide language setting which respects American vs. British spelling (e.g., try running <code>locale</code> at the console). There's no reason the firefox package shouldn't pick this up.

---

### Post by brumman on 2010-04-29
I am new to ubuntu and still trying to find my way. I live in Canada and found that there is no English (canada) dictionary in OO but the US version is loaded by default! So I have changed to the English UK setting and the dictionary and auto spell-check work perfectly; however the **Thesaurus** is missing! I have to revert to US English if I want to have the thesaurus functional - exactly the reverse situation as Ron had - and then add "proper" spellings like Colour as they arise, but of course the spell check will not then pick up color etc as errors.
So is there a way I can add the thesaurus to OO using UK English? 
At the moment my machine is not online and I'd have to download to a portable USB drive from my windows 2000 machine! Remember any instructions need to be at absolute beginner level. LOL
For example I don't understand **clconway's** statement "try running <code>locale</code> at the console" ??

---

