---
title: "desktop and window problems..."
date: 2009-10-03
forum: Desktop Environments
---

### Post by ricardopresto on 2009-10-03
Hi
 I have two small problems with UNR 9.04. Firstly, I can't get icons to appear on the desktop. They've appeared in the 'Desktop' directory, but not on the desktop.:confused: Secondly, is there a way to make applications open in unmaximised windows by default? At the moment, every time I open a program I have to right-click it's tab on the panel and select 'Unmaximise' in order to get the titlebar to display. 

Any help would be much appreciated. I can't believe that I can't figure these things out myself but I've been trying for two days now!

---

### Post by ibuclaw on 2009-10-03
Not sure if UNR uses Nautilus (I think it does), but the way to do it usually is:
[LIST=1]
[*]Press **Alt+F2**
[*]type in:
```
gconf-editor
```
and press Run.
[*]Browse to **/apps/nautilus/preferences/show_desktop** in the conf editor, and ensure that the "show_desktop" checkbox is checked.
[*]Logout/Login.
[/LIST]

And secondly, not sure if Metacity can do this, but compiz has "Window Rules" feature called "no_maximise_match" which forces applications that match a certain criteria to not be maximised.

Regards
Iain

---

### Post by ricardopresto on 2009-10-03
Thanks for replying Iain. I really thought you'd cracked it there. Opened Config Editor, looked at Nautilus/Preferences and, sure enough the box was unchecked. Checked it, re-booted and...still doesn't work. I don't suppose you've any other ideas?

Regards
Richard

---

### Post by ricardopresto on 2009-10-03
Sorted. :P

Reading around some of the forums here I started to suspect that Nautilus had somehow been disabled. Don't know how that happened, but somehow it must have been. Re-enabled Nautilus and the desktop icons appeared. Thank %&£* for that...

---

