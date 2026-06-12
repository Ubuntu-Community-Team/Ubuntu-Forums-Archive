---
title: "Spell Checker Confusion"
date: 2009-02-03
forum: General Help
---

### Post by AC-BC on 2009-02-03
In my newly installed Ubuntu 8.10, I noticed that I was being flagged for incorrectly spelled words that I KNEW were correctly spelled.  After a while, I realized that the spell-checker was using UK spellings, rather than US spellings.

I went to System Settings --> Regional & Language --> Spell Checker, and checked the settings.  They were all set correctly, to US English.

So, why is my system using a UK English dictionary?  How can I fix this?

---

### Post by dcstar on 2009-02-03
> **AC-BC said:**
> In my newly installed Ubuntu 8.10, I noticed that I was being flagged for incorrectly spelled words that I KNEW were correctly spelled.  After a while, I realized that the spell-checker was using UK spellings, rather than US spellings.

I went to System Settings --> Regional & Language --> Spell Checker, and checked the settings.  They were all set correctly, to US English.

So, why is my system using a UK English dictionary?  How can I fix this?

What package are you referring to?

---

### Post by fragos on 2009-02-03
This is a bug in gedit where you need to select specific English location every time you run to get US English dictionary.

---

### Post by AC-BC on 2009-02-03
> **dcstar said:**
> What package are you referring to?

dcstar, what do you mean "what package?"

It came on a two-sided DVD, in a magazine (one side was 32-bit, the other 64-bit; I loaded the 64-bit). Kernel 2.6.27-7-generic if that helps.

fragos, it is not evident on only gedit.  I notice it most in Firefox; which is also correctly set to US English.

---

### Post by fragos on 2009-02-03
I filed a bug on this issue with gedit and it was confirmed. I grew tired of Firefox performance and crashes so I changed to Epiphany which is set for US and works. OpenOffice also has a specific parameter for language and it's set to US English and works. There are at least 5 different regional English dictionaries. I've also seen combination US British dictionaries which makes little sense to me -- some spellings are different. Other than the US the other regional English dictionaries have more of a British connection than we do. I looked through the Configuration Editor and the System Preferences and couldn't find a system wide setting for language -- just in individual applications.

---

### Post by AC-BC on 2009-02-04
Oh.

But isn't there a common dictionary file?  Or does every app have it's own dictionary file (like Windows apps)?  {I thought Linux did things a little smarter than Winbloats.}

Barring that, I guess I'm stuck with it as is.

OK.  Thank you.

---

### Post by fragos on 2009-02-04
There's more than one dictionary system. And each system may have it's own set of dictionary files. Normally only one system is installed and used although Open Office has it's own because it runs on a number of OS platforms. Applications can individualy select what language to use regardless. It's getting more common for multiple languages to be used on a single system.

---

### Post by mb_webguy on 2009-02-04
The system language settings generally only apply to the OS and desktop environment.  Applications like Firefox and OpenOffice have their own language settings independent of the system settings.  This allows multilingual users to have different languages set for different tasks -- for example browsing the web in English while typing documents in French, without having to change the system-wide settings (which may be in Vietnamese).

---

### Post by AC-BC on 2009-02-05
While browsing through the packages offered, I noticed a couple of English packages that were not loaded:
```
language-pack-en
language-pack-kde-en
```
So, I installed them.  I have yet to see a change, but maybe some things need to be restarted before they are applied.  I may find out tomorrow if they are helpful in solving this problem.

However, three other packages got removed in the process:
```
language-support-en
language-support-writing-en
hunspell-en-us
```
We'll see.  :-\

---

