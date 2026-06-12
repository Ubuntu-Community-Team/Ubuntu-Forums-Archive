---
title: "CCSM I've lost the preferences"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by MickS on 2007-10-24
I was messing about with the settings in CCSM and now I can't go to preferences which I need in case I want to disable Compiz, I think I clicked on the minus button and removed the default plugins thing next to the import export buttons, I've tried uninstalling and reinstalling CCSM but that didn't work. I'm using KDE and the effects  still function.
TIA

Mick

---

### Post by MickS on 2008-01-26
I still haven't managed to fix this problem, I have tried apt-get remove purge and then reinstalling but it stays the same.
If I run CCSM in the terminal it give me this error report but I don't know what to make of it.
Any clues what to do next?  BTW I'm on KDE Gutsy and compiz works fine as does CCSM I just can't go to preferences:confused:

mick@mick-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 403, in ShowPreferences
    preferencesPage = PreferencesPage(self, self.Context)
  File "/usr/lib/python2.5/site-packages/ccm/Pages.py", line 1231, in __init__
    self.ProfileBackendPage = ProfileBackendPage(main, context)
  File "/usr/lib/python2.5/site-packages/ccm/Pages.py", line 850, in __init__
    index = self.Context.Profiles.values().index(self.Context.Profiles[name])
KeyError: 'test'


TIA

Mick

---

