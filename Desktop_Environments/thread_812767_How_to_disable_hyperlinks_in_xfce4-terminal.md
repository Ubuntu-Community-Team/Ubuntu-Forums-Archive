---
title: "How to disable hyperlinks in xfce4-terminal?"
date: 2008-05-30
forum: Desktop Environments
---

### Post by Kennet on 2008-05-30
Can someone please help me with how I disable the hyperlink "feature" in xfce4-terminal. I cannot find anything in the terminalrc file nor do I have found anything on the net despite searching for almost two hours. The closest to anything useful I found was a note on the xfce4 page that stated it was possible to disable it but not anything on how it is done. I did search this forum too but I found nothing useful here, it may still exist though I didn't find it.

Regards

---

### Post by oschad on 2009-06-10
To disable the highligthing of URLs in xfce terminal, use the setting 'MiscHighlightUrls=FALSE' in your terminalrc file

regards
oli

---

### Post by rickyrockrat on 2010-12-03
For those of you, like me, who didn't know where it terminalrc can be found, use man xfce4-terminal and you will find it is in $XDG_CONFIG_DIRS/Terminal/terminalrc

Which on standard installs is ~/.config/Terminal.

---

