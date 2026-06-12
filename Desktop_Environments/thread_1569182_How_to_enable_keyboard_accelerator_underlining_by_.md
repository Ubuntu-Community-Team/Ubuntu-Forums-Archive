---
title: "How to enable keyboard accelerator underlining by default"
date: 2010-09-06
forum: Desktop Environments
---

### Post by jkirby on 2010-09-06
I just upgraded from Jaunty Jackalope to Lucid Lynx.
I prefer to have the Keyboard Accelerators underlined at all times. 
That is, I don't want them hidden until I press Alt.
Keyboard accelerators aren't accelerating my work if I have to wait a second or two to read what the underlined letter is after I press the Alt key.
On Windows there's a setting for this (Control Panel, Display, Appearance, Effects, Hide Underlined letters).

Where can I set this in Ubuntu?

I read that setting gtk-enable-mnemonics=1 in a ~/.gtkrc or ~/.gtkrc-2.0 file should do it. I tried that. Doesn't work.

I read that Ubuntu Tweak has a setting for it.  I installed Ubuntu Tweak. I couldn't find the setting.

Anyone have any ideas?

---

### Post by ethridgela on 2010-10-06
The best way I've found to keep the keyboard accelerators visible is to change the "Controls" to a set used by an older theme.

To do that, go to System | Preferences | Appearance.  In the Appearance dialog box, click the "Customize" button.  Under the "Controls" tab, select "Glossy", or "Glider".  (Other older themes may work equally well.)

Close the dialog boxes, then close and restart Nautilus to test it.

---

### Post by virtual reality on 2010-12-10
I'd like to bump! the issue.

I, too, would always like to see the underlined letter by default.

vr.

---

### Post by juanhernandezgomez on 2011-02-07
This is not the first time I tried to change that but I couldn't find it how. Finally found it today.

Thanks to ethridgela to point me in the right direction. I didn't know it was enabled in other themes (Clearlooks for example) so knowing that it was possible it was a matter of finding where it was defined.

If you edit the following file of your theme (I was using Ambiance theme):
```
/usr/share/themes/Ambiance/gtk-2.0/gtkrc
```
Enter the following entry if it doesn't exist:
```
gtk-auto-mnemonics = 0
```
Put it to 0 to display the accelerator always.

For reloading the configuration I just selected a different theme in the System / Preferences / Appearance dialog and closed the dialog. Then repeated the same selecting my original theme (Ambiance). Or if you prefer you can logout of your session ... sorry I don't know other way of reloading the configuration.

This setting would be for all the users using that theme. I tried putting that on my ~/.gtkrc-2.0 file but it doesn't override the value if it already exists in the gtkrc file. If the value is not defined in the theme it works but I don't know how to override it. Anyway it works that way.

Hope it helps.
Juan

---

### Post by erjoalgo on 2011-06-12
nice job

---

