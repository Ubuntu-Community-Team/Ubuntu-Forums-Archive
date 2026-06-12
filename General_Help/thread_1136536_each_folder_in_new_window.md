---
title: "each folder in new window"
date: 2009-04-25
forum: General Help
---

### Post by volter on 2009-04-25
sorry about so newbie question but ,how can I do that each time I open folder it will opens in new window?

---

### Post by _Purple_ on 2009-04-25
Go to Edit > Preferences. In Behavior tab, uncheck Always open in browser windows.

---

### Post by dcstar on 2009-04-25
> **volter said:**
> sorry about so newbie question but ,how can I do that each time I open folder it will opens in new window?

Disabling the Nautilus option "Always open in browser windows" is supposed to do this, but it doesn't seem to make any difference (on my system) if it is enabled or not.

Some other may want to try it to see if it is a bug.

---

### Post by _Purple_ on 2009-04-25
> **dcstar said:**
> Disabling the Nautilus option "Always open in browser windows" is supposed to do this, but it doesn't seem to make any difference (on my system) if it is enabled or not.

Some other may want to try it to see if it is a bug.

I am using intrepid and it works for me. You have to close all the windows after disabling it and open it again.

---

### Post by dcstar on 2009-04-25
> **_Purple_ said:**
> I am using intrepid and it works for me. You have to close all the windows after disabling it and open it again.

Nope, I have a /home from 8.04 and it still doesn't work - but if I create a brand new account it does work!

There must be some legacy Gnome settings that are preventing the correct behaviour with the new version.

---

### Post by volter on 2009-04-25
thnx.

---

### Post by dcstar on 2009-04-25
> **dcstar said:**
> Nope, I have a /home from 8.04 and it still doesn't work - but if I create a brand new account it does work!

There must be some legacy Gnome settings that are preventing the correct behaviour with the new version.

Ahh ha!, I found that the launcher that I have in my top panel always opens Nautilus in a specific mode that bypasses this setting (--browser %U).

Opening from the "Places" menu works as it is supposed to with this setting.

---

