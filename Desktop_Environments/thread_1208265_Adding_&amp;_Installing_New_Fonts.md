---
title: "Adding &amp; Installing New Fonts"
date: 2009-07-09
forum: Desktop Environments
---

### Post by abevrnja on 2009-07-09
Hi there.

I'd like to know what is the difference in adding a new font and installing one.
Also, I added some font files in **/usr/share/fonts/** and when I go to **Sysyem > Preferences > Appearance > Fonts** I can find them but Open Office Word Processor doesn't seem to recognize them. I suppose I should do something to make it work but I don't know what. (There looks to be some kind of difference between fonts used by system and those used by different applications)

Thanks in advance :D

---

### Post by rgsproductions on 2009-07-15
I was having the same issue.  I found this at [www.linuxforums.org](www.linuxforums.org)  

"In GNOME you can open Nautilus and type fonts:/// in the address bar and simply drop them in there, once X is restarted they should work. Or you can put them in a proper dir in /usr/share/fonts yourself and they should work as well when X is restarted."

It worked for me!  Hope it helps you.

[http://www.linuxforums.org/forum/installation/38154-how-install-fonts.html](http://www.linuxforums.org/forum/installation/38154-how-install-fonts.html)


I re-read your question and I don't think I helped.  I checked in OpenOffice and all the fonts I added showed up in the font selection.

---

### Post by AZzKikR on 2009-07-15
> **abevrnja said:**
> Also, I added some font files in **/usr/share/fonts/**

Just an idea:

You can also place your fonts into ~/.fonts/ instead of /usr/share/fonts/. This will have a few benefits, like: no sudo to place the fonts there, and  you'll only have to backup the /home/$USER directory and you have all your fonts again.

Then again, the fonts are only available to only that specific user, iirc.

---

