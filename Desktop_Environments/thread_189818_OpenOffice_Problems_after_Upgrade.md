---
title: "OpenOffice Problems after Upgrade"
date: 2006-06-05
forum: Desktop Environments
---

### Post by bardu on 2006-06-05
Hi friends,

after upgrading Ubuntu OpenOffice was vanished from my machine. So, I installed it again using synaptic. Now I have the problem that the Spellchecker doesn't work anymore. 

Has someone an idea how to fix it?

Thanks in advance.
Stephan

---

### Post by bardu on 2006-06-05
Okay, fixed it.

---

### Post by murataht on 2006-06-05
[QUOTE=bardu]Okay, fixed it.[/QUOTE]
if you could explain how you fixed it, it could help others with the same problem. :wink:

---

### Post by todoporron on 2006-06-05
Yeah... how did you solved this?

---

### Post by bardu on 2006-06-06
Sorry for not explaining the fix.
The default language on my machine is Canadian English. The Openoffice installation also used this setting, but it seems there is no spellchecker for Canadian English available. So. I went to Openoffice Tools --> Options --> Language Settings --> Languages and set the "Default languages for documents - Western" property to English(USA). It is in some way different to Canadian English, but will do the job for most cases. 

Hope that will help.
Stephan

---

### Post by bruceliz on 2006-07-03
[QUOTE=bardu]it seems there is no spellchecker for Canadian English available.[/QUOTE]

For OpenOffice.org there's none in Ubuntu, but you can do the following:

Via application menu go to File -> Wizards -> Install new dictionaries...

Use that 'wizard'  to select and install Canadian dictionaries (and hyphenation rules and thesaurus, if you like -- I think the hyphenation rules are actually UK, and the thesaurus actually US). These are installed your home directory's '.openoffice2/user/wordbook' directory.

Go to Tools -> Options -> Language Settings -> Writing Aids.

In pane 'Available language modules', select 'OpenOffice.org Hunspell SpellChecker'. Click Edit, set language as 'English (Canada)', make sure 'Spelling' box is checked.

Go to  Tools -> Options -> Language Settings -> Languages, and ensure 

   Locale setting
   Default currency
   Default languages for documents

are all set to 'English (Canada)'.

Spellchecking should now use Canadian dictionary (and hyphenation rules and thesaurus if you've installed them via the Wizard and selected them). Of course the dictionary-installer will install whatever dictionaries the user needs/chooses from among those available.

---

### Post by tarek on 2007-06-16
> **bruceliz said:**
> For OpenOffice.org there's none in Ubuntu, but you can do the following:

Via application menu go to File -> Wizards -> Install new dictionaries...

Use that 'wizard'  to select and install Canadian dictionaries (and hyphenation rules and thesaurus, if you like -- I think the hyphenation rules are actually UK, and the thesaurus actually US). These are installed your home directory's '.openoffice2/user/wordbook' directory.

Go to Tools -> Options -> Language Settings -> Writing Aids.

In pane 'Available language modules', select 'OpenOffice.org Hunspell SpellChecker'. Click Edit, set language as 'English (Canada)', make sure 'Spelling' box is checked.

Go to  Tools -> Options -> Language Settings -> Languages, and ensure 

   Locale setting
   Default currency
   Default languages for documents

are all set to 'English (Canada)'.

Spellchecking should now use Canadian dictionary (and hyphenation rules and thesaurus if you've installed them via the Wizard and selected them). Of course the dictionary-installer will install whatever dictionaries the user needs/chooses from among those available.


Thanks! I've been looking for a solution since I upgraded to Feisty.

tarek

---

### Post by Hagar Delest on 2007-06-17
Hi All,

For further information about spell checking, I've made a tutorial here : [[Tutorial] Spell check and Language configuration](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=758).

---

### Post by The Pinny Parlour on 2007-06-23
Unfortunately this doesn't work.  Open is great but enabling real time spell check is the worst thing about it.  Bloody hopeless it is.

---

### Post by Hagar Delest on 2007-06-23
> **The Pinny Parlour said:**
> Unfortunately this doesn't work.
What's the problem ? We need information to help you. What's the language in the paragraph style properties (*Font* tab) ?

---

