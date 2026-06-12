---
title: "last kernel splash"
date: 2006-06-17
forum: Desktop Environments
---

### Post by NoWhereMan on 2006-06-17
after last kernel update. on "preparing restricted drivers" the boot splash goes away and I jump into the text-mode boot

also, a while later, the vt596 says something about updating the bios and set force=1 (i don't know what this is about, but I don't think it's related; I think this already were there before)

thank you

---

### Post by NoWhereMan on 2006-06-18
bump (sorry)

---

### Post by mlind on 2006-06-18
Does some sort of error logged on screen when usplash fallbacks to text-mode?
It could be nothing to worry about, but does dmesg contain warning/error you're describing?

---

### Post by NoWhereMan on 2006-06-18
these are the only errors that are actually shown during boot

```

[17179608.520000] vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1
[17179608.944000] via686a 0000:00:07.4: base address not set - upgrade BIOS or use force_addr=0xaddr

```

but they appear *after* it's already turned into text mode

---

### Post by Fausto on 2006-06-18
[QUOTE=NoWhereMan]these are the only errors that are actually shown during boot. But they appear *after* it's already turned into text mode[/QUOTE]

I think **that is the way it works**. That's not a problem, only the **natural "trace error"** delay (between "error" and "trace it") 

[I]Am I pointing right your question? I' m just guessing and trying to understand you
[/I]

Good Luck !!

---

### Post by Fausto on 2006-06-18
[QUOTE=NoWhereMan]these are the only errors that are actually shown during boot. But they appear *after* it's already turned into text mode[/QUOTE]

I think **that is the way it works**. That's not a problem, only the **natural "trace error"** delay (between "error" and "the error trace-secure delay") 

[I]Am I pointing right your question? I' m just guessing and trying to understand you
[/I]

Good Luck !!

---

### Post by NoWhereMan on 2006-06-18
Maybe that's the problem, then. I wonder how to fix it now :confused:

---

### Post by NoWhereMan on 2006-08-30
found the answer [http://ubuntuforums.org/archive/index.php/t-75132.html](http://ubuntuforums.org/archive/index.php/t-75132.html)

---

