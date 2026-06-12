---
title: "possible bug? &quot;cat /var/run/utmp&quot;"
date: 2008-03-19
forum: Desktop Environments
---

### Post by confy on 2008-03-19
Hello guys...
Can you type in your terminal '**cat /var/run/utmp**' ?
You will see bunch of gibberish !

There is no harm by typing this command, i just want to confirm if it is bug or i'm missing something....

---

### Post by xuande on 2008-03-19
> **confy said:**
> Hello guys...
Can you type in your terminal '**cat /var/run/utmp**' ?
You will see bunch of gibberish !

There is no harm by typing this command, i just want to confirm if it is bug or i'm missing something....

The format of utmp is binary, so it's expected for it to be gibberish on your terminal.  Programs like 'w' interpret it for you.

---

### Post by confy on 2008-03-19
yeah i know but the problem is, how do i return to normal prompt without logging out or closing windows?

---

### Post by xuande on 2008-03-19
The 'reset' command sometimes works, depending on how far gone your terminal emulator is.  The problem is that arbitrary binary strings are interpreted by the emulator as control codes that put it in strange modes.

---

### Post by confy on 2008-03-19
hey that's very nice tip!

sometimes i work with unicode files and i get same gibberish as here, the "reset" command is what i was looking for!

Thank you!

---

