---
title: "shift + &lt;numpad arrow key&gt; behavoir"
date: 2005-08-27
forum: Desktop Environments
---

### Post by klim on 2005-08-27
Hello!

Can I configure my X server to behave like Windows when I press shift + <numpad arrow key>?
For example, when I press ctrl+shift I expect X to paste some text from clipboard, but it prints "0".

---

### Post by sneeman on 2007-12-04
I know this is an old post, but it needs an answer. Took me forever to find this:

Add the following to your xorg.conf file (/etc/X11/xorg.conf) under the keyboard section:

```
Option		"XkbTypes"	"default+numpad(microsoft)"
```

For example:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	**Option		"XkbTypes"	"default+numpad(microsoft)"**
EndSection

```

That makes the numpad act like Windows, so when you do shift-numpad4 it selects the character to the left, etc.

I'm running kubuntu 7.10, so I don't know if this is the same for gnome, but it should be.

Found this at [http://forums.gentoo.org/viewtopic.php?t=47846]("http://forums.gentoo.org/viewtopic.php?t=47846")

---

### Post by BlackBaron1024 on 2008-06-23
The line:
```
	Option		"XkbTypes"	"default+numpad(microsoft)"

```
didn't work for me. It changed my numpad to a permanent nunlock (i.e. always numbers).
Browsing [here]("http://archive.netbsd.se/?ml=arch-dev-public&a=2008-02&t=6473056"), I found the idea of trying this instead:
```
	Option		"XkbOptions"	"numpad:microsoft"

```
and it worked perfectly.

Tip: You can restart the graphics environment with ctrl+alt+backspace to check the results, instead of restarting the whole system.

---

### Post by BlackBaron1024 on 2008-06-24
I just found out in:

System -> Assistive Technologies
-> Keyboard Accesibility -> Layouts
-> Layout Options -> Miscellaneous compatibility options

there's an option to fix this.

---

