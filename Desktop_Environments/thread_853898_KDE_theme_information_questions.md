---
title: "KDE theme information questions"
date: 2008-07-09
forum: Desktop Environments
---

### Post by dbbolton on 2008-07-09
I would like to know how KDE (3.5 and 4) store information about the user interface, such as the QT style, Kwin theme, icon theme, and so on. Specifically, I want to know whether this info is stored in a file somewhere (like ~/.kde perhaps).

Does anyone know?

---

### Post by GeneralZod on 2008-07-09
> **dbbolton said:**
> I would like to know how KDE (3.5 and 4) store information about the user interface, such as the QT style, Kwin theme, icon theme, and so on. Specifically, I want to know whether this info is stored in a file somewhere (like ~/.kde perhaps).

Does anyone know?

~/.kde/share/config/kdeglobals contains a lot of this stuff.  The kwin theme is in ~/.kde/share/config/kwinrc.

---

### Post by dbbolton on 2008-07-09
> **GeneralZod said:**
> ~/.kde/share/config/kdeglobals contains a lot of this stuff.  The kwin theme is in ~/.kde/share/config/kwinrc.
Thanks.

Would you happen to know where the font for Konsole is stored?

---

### Post by GeneralZod on 2008-07-09
> **dbbolton said:**
> Thanks.

Would you happen to know where the font for Konsole is stored?

~/.kde/share/config/konsolerc, I guess :)

---

### Post by dbbolton on 2008-07-09
> **GeneralZod said:**
> ~/.kde/share/config/konsolerc, I guess :)
That's what I suspected, but this is all I have in that file:

```

[$Version]
update_info=konsole.upd:kde2.2/r1,konsole.upd:kde3.0/r1

[Desktop Entry]
AllowResize=false
BlinkingCursor=false
CtrlDrag=true
CutToBeginningOfLine=false
EnableBidi=false
LineSpacing=0
MatchTabWinTitle=false
SilenceSeconds=10
TerminalSizeHint=false
WarnQuit=true
XonXoff=false
has frame=true
schema=Transparent_darkbg.schema
wordseps=:@-./_~

[TipOfDay]
RunOnStart=false
TipLastShown=2008,7,1,0,23,6

```

---

