---
title: "Open Office 2, can't change the spellcheck language"
date: 2005-10-16
forum: Desktop Environments
---

### Post by DanN on 2005-10-16
I know this is a minor issue, but I've just been writing a document using OO2 under a fresh breezy install and the spellchecking is set to US english by default, so I went to change it to the GB english and kept on writing, but it kept identifying all my -isations and -ours (as opposed to -izations and -ors) as misspelled.  So I checked and it is was still set to GB in the options menu, but when I run the actual spellchecker it says its using US english and if I change it to UK it doesn't stick.  Anyway if anybody figures out why this is happening I'd love to know.
Cheers

---

### Post by Manny C on 2005-10-16
Need to ensure that the default language is EN-GB. Namely, hit F11. This brings up the Styles and Formatting pane. Right click Default and select Modify. Go to the Font tab and change the language to English (UK).

If you want to change this setting permanently and not just in one particular document, you need to set up a template based on a blank documents settings. So create a new document. Change the font/language settings as you so desire. Then select File>Templates>Save. Type in the template name (whatever you like). Then File>Templates>Organise. Expand the My Templates pane and right click the Template you created and select Set as Default Template.

---

### Post by DanN on 2005-10-17
Hey thanks for the advice, I didn't actually know about that stuff, when I changed the language I went to Tools > Options then into Language Settings > writing aids, edited the 'OpenOffice.org MySpell SpellChecker' and changed language to Enslish UK.  Unfortunately, neither that method nor the one you described worked however, it's still not 'autochecking' in the right language and when I do a spellcheck from the menu it always comes up as US English even though I've tried to change it.  Anyway, thanks for the advice.

---

