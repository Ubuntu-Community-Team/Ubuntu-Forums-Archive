---
title: "window borders dissapeared"
date: 2009-01-22
forum: General Help
---

### Post by simtaalo on 2009-01-22
all my window borders have dissapeared, i can't drag an app window around unless i go into my taskbar and right-click 'move'

i've attached a screenshot


any help much appreciated :)

---

### Post by Crafty Kisses on 2009-01-22
Not sure if you're running Emerald or something, but try one of the following commands:
```
emerald --replace
```
The other option, is to revert back to Metacity, you can do that by doing the following:
```
metacity --replace
```

---

### Post by simtaalo on 2009-01-22
kinda worked, they come back after a reset, but if i launch firefox it does the same thing unless i press F11 a couple of times.

---

### Post by Crafty Kisses on 2009-01-22
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager and find "Windows Decorations" add the following line to "Decoration Windows":

```
(any) | class=Firefox
```

Once you've done that close out CCSM, then open CCSM back up again, then change that to:

```
any
```

Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:

```
metacity --replace
```

I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal. The issue really only occurs when Firefox crashes and you reboot it, but those are the fixes and I've tested them myself and they do actually work.

---

### Post by Yashiro on 2009-01-22
System Menu, Preferences, Appearance, Visual Effects.
Turn desktop effects off then back on.

*metacity --replace &* often does not work with compiz running.

Also stop running nspluginwrapper(npviewer.bin). :P

---

### Post by simtaalo on 2009-01-23
> **Yashiro said:**
> 
Also stop running nspluginwrapper(npviewer.bin). :P

what does npviewer.bin do?

---

### Post by Yashiro on 2009-01-23
nspluginwrapper runs your legacy 32bit plugins.
npviewer.bin is the process it runs in. A hidden process that runs stuff like Flash movies.

However, it is bugged and causes slowdowns and crashes.
If you're on 64bit Ubuntu, uninstall nspluginwrapper and old flash plugins etc. Start using the 64bit versions.

---

