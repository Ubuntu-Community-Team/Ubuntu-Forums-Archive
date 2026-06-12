---
title: "Middle Click in Firefox"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Night on 2005-12-03
Hey I just updated my firefox to 1.5 and now when I middle click it tries to open the link in a new tab. I want to change this back to how it worked in firefox 1, where when you middle click on a tab it tries to close it and the rest of the time it doesnt do anything. Any help?

---

### Post by invalid on 2005-12-03
I believe you can change the behavior by pointing your browser to "about:config"

---

### Post by trevorv on 2005-12-03
If you go to about:config and filter "middle", set browser.tabs.opentabfor.middleclick to false and middlemouse.contentloadURL to false, that *should* do the trick I think. If it doesn't, change them back in case I've given you the wrong ones.

---

### Post by Night on 2005-12-03
thanks. that worked

---

### Post by raghav_p on 2005-12-28
I have an interesting scenario to report. I changed the firefox setting for middleclick; it changes for the session but if I close firefox and restart it, the preference is gone. Any ideas about this?

---

### Post by gent_k on 2006-01-04
Hey, I'm new here. (and to linux)

I updated to 1.5 too, and now I can't close tabs by middle-clicking them.  Opening new tabs works as expected, but doing what's suggested above disables that, so I think browser.tabs.opentabfor.middleclick should stay 'true', and only change middlemouse.contentloadURL to false.

[edit] that's how it works for me anyway

---

