---
title: "US Keyboard, accented characters, programming, entering a &quot; -- life after us_intl"
date: 2006-01-08
forum: General Help
---

### Post by wfjm on 2006-01-08
I use a US keyboard, need sometimes accented characters when writing letters, but while programming, want to type ' or " without extra strokes. For years I switched between "us" (programming mode) and "us_intl" (letter mode) with the KDE Keyboard Tool and got my work done.

The new version of the KDE Keyboard setup classifies "us" and "us_intl" as two layout variants of the same keyboard. One can not generate a configuration which allows to choose with the Keyboard Tool between the "basic" and "alt-intl" layout. This is already much discussed in various forums.

I haven't yet figured out how to produce simple ASCI quote (code 22) characters with the "alt-intl" layout in system with a default UTF-8 locale setting. Hitting " twice yields a UTF-8 code c2 a8.

Currently I'm switching the keyboard modes simply with the shell commands
```
setxkbmap -model pc104 -layout us -variant basic
setxkbmap -model pc104 -layout us -variant alt-intl
```

Questions:
[LIST]
[*]is there a better way to handle keyboard layouts ?
[*]how to enter plain " and ' ect characters when in alt-intl mode ?
[/LIST]

Any suggestions very welcome.

---

