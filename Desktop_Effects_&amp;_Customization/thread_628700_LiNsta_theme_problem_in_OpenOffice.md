---
title: "LiNsta theme problem in OpenOffice"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by mulder_edu on 2007-12-01
I just installed the LiNsta theme in Gutsy.  Everything works great except in OpenOffice.  Normally I have icons and such in the toolbars.  Now it's all words.  Looks kind of like a foo-bar'd attempt to make it look like M$ Office 2007.  Any way to change it back?  Changing the options on the Interface tab in Appearance Preferences makes no difference.

See screen shot:

---

### Post by mulder_edu on 2007-12-01
Urgh, reinstalling OpenOffice didn't fix it either.  Now the theme wont even apply to it.  It just has the text without the icons.:confused:

---

### Post by FuturePilot on 2007-12-01
Go Tools>Options>View. Where it says Icons and Styles change it from Automatic to something else.

---

### Post by SunnyRabbiera on 2007-12-01
also there is a pixmap related issue to this, plus i think this is an issue with linista in general

---

### Post by mulder_edu on 2007-12-01
Yeh, that's what I thought.  Tried it.  Didn't make a difference.  As far as I can tell, OpenOffice says it's displaying correctly.  It obviously is not.

> **FuturePilot said:**
> Go Tools>Options>View. Where it says Icons and Styles change it from Automatic to something else.

---

### Post by FuturePilot on 2007-12-01
Hmm. That's odd. Does it work normally with any other theme? Or is this the only one? If you change a theme make sure to restart OO if it was open when you changed the theme.

---

### Post by mulder_edu on 2007-12-01
I tried switching to a different theme.  The LiNsta colors obviously go away, but the button problem stays.

> **SunnyRabbiera said:**
> also there is a pixmap related issue to this, plus i think this is an issue with linista in general

---

### Post by mulder_edu on 2007-12-01
It used to work with other themes, but now the problem wont go away, dosen't matter the theme.  I reinstalled OO (restarted and everything of course).

> **FuturePilot said:**
> Hmm. That's odd. Does it work normally with any other theme? Or is this the only one? If you change a theme make sure to restart OO if it was open when you changed the theme.

Take a look at it now, with human as theme.  Notice that the colors are wrong now?  They don't change, no matter the theme.

---

### Post by FuturePilot on 2007-12-01
Try creating a new profile
Close OO then do this
```
mv .openoffice.org2 .openoffice.org2_old
```

---

### Post by mulder_edu on 2007-12-01
Genius!  Thanks.  That fixed it.  What could have caused that?

---

### Post by FuturePilot on 2007-12-01
> **mulder_edu said:**
> Genius!  Thanks.  That fixed it.  What could have caused that?

Great! Not sure what could have done that. Might have just gotten randomly corrupted or something.

---

