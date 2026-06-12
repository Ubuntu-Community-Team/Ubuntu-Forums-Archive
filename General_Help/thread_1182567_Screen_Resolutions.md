---
title: "Screen Resolutions"
date: 2009-06-09
forum: General Help
---

### Post by chebbie on 2009-06-09
hey guys i'm having a problem pertaining to my screen resolution.

i've set my resolution by 1600x1200 and I applied the setting.
each time i swtich off my PC and switch it on back again, the resolution goes to 'Auto' and my display changes since apparently it uses another resolution.

my graphics card can support the 1600x1200 resolution but i just don't know what's the matter.


When I click to Save to X configuration file it gives me this:

unable to create new X config back up
file '/etc/X11/xorg.conf.backup'.

---

### Post by suffice on 2009-06-09
I used to have that problem a long time ago with feisty or gutsy.   Check the file permissions on that xorg.conf file, or run the settings manager as sudo....I think that worked for me a long time ago.

---

### Post by chebbie on 2009-06-09
can you simply your answer please cause im very very new to linux only 3 days..where to look for those files you're talking about??

---

### Post by ChaiTan on 2009-06-09
I'm assuming you have an nvidia graphics card.
Press Alt-F2 and type
```
gksudo nvidia-settings
```
and then make the changes and click on "Save to X configuration file"

---

