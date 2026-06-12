---
title: "Mapping keyboard volume keys?"
date: 2008-07-14
forum: Desktop Environments
---

### Post by kooldino on 2008-07-14
I've got a Microsoft Keyboard with the special dedicated volume keys on it.

Where do I go to map them so they're usable?  

I couldn't find anything obvious under the keyboard & mouse setup in System Settings.

---

### Post by KuriKai on 2008-07-14
"keyboard shortcuts" under "system"/"preferences"

---

### Post by kooldino on 2008-07-14
I can't find it there.

This on on KDE, mind you.

---

### Post by Naegling23 on 2008-07-15
Im not at my kde desktop right now, so I cant tell you exactly where they are.

Under your system settings, there is a keyboard and or mouse setting section.  The option to change the keys is there somewhere.  Your just going to have to poke around your system settings for a little while, but trust us, they are there.

---

### Post by fatbuttlarry on 2008-07-27
In KDEs keyboard shortcuts (Kubuntu 8.04) there are three main categories: [LIST]
[*]Schemes
[*]Commands
[*]Modifiers.
[/LIST]

**Commands** is for launchers, **Modifiers** is for overriding X11 mappings, so [COLOR="Red"]**Schemes**[/COLOR] is the winner.

Under **Schemes**, there are 3 main categories:
[INDENT][LIST]
[*]Global
[*]Sequences
[*]Application.
[/LIST][/INDENT]

**Sequences** is for desktop switching, **Application** is for "File --> Edit" related stuff, so [COLOR="Red"]**Global**[/COLOR] is the winner.

Under **Global** there are 5 main categories: 
[INDENT][INDENT][LIST]
[*]System
[*]Panel
[*]Desktop
[*]Clipboard
[*]Keyboard.
[/LIST][/INDENT][/INDENT]

**System** does not contain anything relating to volume or multimedia controls.
**Panel** does not contain anything relating to volume or multimedia controls.
**Desktop** does not contain anything relating to volume or multimedia controls.
**Clipboard** does not contain anything relating to volume or multimedia controls.
**Keyboard** does not contain anything relating to volume or multimedia controls.

Opening **AmaroK**, **there are Volume Up/Volume Down entries** under "Settings --> Configure Global Shortcuts", but this volume shortcut is for AmaroK only and **does not affect System volume**.

Thanks kindly for the help Naegling23 and KuriKai, however from my findings, the option to change this is not in the area suggested "System Settings --> Keyboard and Mouse", known on other KDE platforms as "Run --> kcontrol --> Regional and Accessibility --> Keyboard Shortcuts"

The reason I am interested is, I have noticed the increment is 10% by keyboard, but 3% by mouse wheel.  I would like to know how to make these values the same. 

Any insight in doing so would be greatly appreciated!!!

[Desktop screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=79161&d=1217193342") attached for fun!

Thanks!

-Tres

---

