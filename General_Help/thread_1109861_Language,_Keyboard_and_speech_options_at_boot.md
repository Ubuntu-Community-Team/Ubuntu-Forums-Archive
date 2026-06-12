---
title: "Language, Keyboard and speech options at boot?"
date: 2009-03-29
forum: General Help
---

### Post by drbongo on 2009-03-29
I want to make a customised isolinux.cfg file that will allow a blind user to enter a two letter code at the boot prompt e.g. es (for spanish) that will then determine the locale, language, keyboard layout and speech (Orca) etc for the user. Any suggestions?

I can get the language to change by using lang=es and locale=es but no joy with the keyboard layout or Orca speech. I have tried keyboard=es keyb=es iocharset=es and orca=es, but they don't work!

A blind user cannot use the language selection on the GDM screen, because it doesn't support speech.

drbongo

---

