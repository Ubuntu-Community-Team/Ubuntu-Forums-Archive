---
title: "Installing the package - hotkeys - How do I find out what keyboard type I have?"
date: 2005-09-09
forum: Desktop Environments
---

### Post by daller on 2005-09-09
Hi All,

Just installed "hotkeys" but to run it, it requires "-t" - the type of the keyboard...

...How do I find the type of my keyboard? (Its the internal keyboard of An "HP pavilion ze4400")

Anyone of you, using another app to configure the multimedia-keys??? (khotkeys doesn't seem to work!)

---

### Post by Takis on 2005-09-09
I use KHotKeys, and it seems to work fine. Have you set your keys using xmodmap?

[http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)

Follow this up to step 5, then KHotKeys should be able to pick everything up.

---

### Post by daller on 2005-09-10
[QUOTE=Takis]I use KHotKeys, and it seems to work fine. Have you set your keys using xmodmap?

[http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)

Follow this up to step 5, then KHotKeys should be able to pick everything up.[/QUOTE]

oskar@oskar:~$ khotkeys
ERROR: Communication problem with khotkeys, it probably crashed.

---

### Post by Takis on 2005-09-11
```
taki@mrflibble:~$ khotkeys
ERROR: Communication problem with khotkeys, it probably crashed.

```
I get the same thing here - but that's not how I normally open KHotKeys. Try opening Control Centre->Regional & Accessibility->KHotKeys.

---

### Post by daller on 2005-09-12
Never tried Khotkeys before - How do I add multimedia-keys?

---

### Post by Takis on 2005-09-12
See above the above the above the above. :)

---

### Post by daller on 2005-09-13
All the keys are "known" - if that is what you refer to...

...i'm using mmkeys to manage my multimedia-keys - and it works perfectly - just a little geeky to configure...

What I'm asking, is how to setup multimedia-keys in Khotkeys - all I can find is the "normal-keys" section...

---

### Post by Takis on 2005-09-14
Hmmm, I'm afraid I don't really understand what you mean. Could you be a bit more specific?

---

### Post by daller on 2005-09-15
I've never used khotkeys before...

Did this:

Entered khotkeys!

"New Action" -> "Triggers" -> "New" -> "Shortcut trigger" -> "Press None" -> "Press my multimedia play-button - nothing happens"

Hope you see the problem...

---

