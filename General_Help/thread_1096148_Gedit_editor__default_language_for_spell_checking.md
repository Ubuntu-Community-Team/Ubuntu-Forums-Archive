---
title: "Gedit editor  default language for spell checking"
date: 2009-03-14
forum: General Help
---

### Post by burakvarhan on 2009-03-14
Hello,

I am running Ubuntu 8.10. My system language is US English however my keyboard is Turkish layout. Both languages use latin alphabet. I am almost always writing in English but when I wanted to run spellcheck gedit only provides Turkish as an option and there is no button to add English language.

I suspect that gedit makes the language decision based on the keyboard layout not system language. In Windows keyboard layout and system language are different items and you can use different combinations like "Turkish layout and English language".

Is there a way to solve the problem?
Thanks

---

### Post by fragos on 2009-03-14
I've a standard English keyboard and gedit give me a supported list of languages including a generic English, 6 country specific versions of English and Turkish. It always defaults to generic English which isn't correct for the US. Each time I use spellcheck I have to specifically select English(US). There have been bugs reported on this. You're welcome to sign in to launchpad and add your comments and experience with the problem.

---

### Post by dcstar on 2009-03-15
> **burakvarhan said:**
> Hello,

I am running Ubuntu 8.10. My system language is US English however my keyboard is Turkish layout. Both languages use latin alphabet. I am almost always writing in English but when I wanted to run spellcheck gedit only provides Turkish as an option and there is no button to add English language.
.........
Is there a way to solve the problem?
Thanks

Install the **aspell-en** package.

---

### Post by burakvarhan on 2009-03-16
Thank you David, It now works!

---

