---
title: "Keyboard key missing in jaunty"
date: 2009-07-06
forum: Desktop Environments
---

### Post by denni on 2009-07-06
Im using ubuntu 9.04 jaunty with a great success but one thing is bothering me and that is that the key above ctrl [IMG]http://ubuntuforums.org/attachment.php?attachmentid=120106&stc=1&d=1246853749[/IMG]and beside left-shift  is not working at all.   Have tasted this on 3 keyboards.  The language is Icelandic.

---

### Post by denni on 2009-07-06
anyone got answare about a missing key in the keyboard.  Think it is a bug in the keyboard settings in jaunty.

---

### Post by shel-hall on 2009-07-06
> **denni said:**
> anyone got answare about a missing key in the keyboard.  Think it is a bug in the keyboard settings in jaunty.
That physical key (i.e. one to the left of Z) doesn't exist on the US 101-key keyboard, though it does on the French-Canadian one, so it must return a code of some sort if it's there. Somewhere there must be a table that relates scan codes to characters, but where and how, I have no idea.

Do you say "hilsen" in Icelandic?

-Shel

---

### Post by JC Cheloven on 2009-07-06
It seems to be a bug in the locale for your region. The spanish keyboard also has that key in that place, and works alright. Perhaps you should file a bug in launchpad, if not already done. I'm prety sure that this will very easy to fix for the devel team.

---

