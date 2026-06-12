---
title: "pc shuts it's self down"
date: 2006-06-27
forum: Desktop Environments
---

### Post by ghettohacker on 2006-06-27
i've been searching for days for a similar problem occuring to someone else, and havn't really found anything helpful. my pc has a intel celeron - 2.8 ghz
with 256 mb memory.  i recently installed ubuntu 6.06 on a pc that had been running win-xp home edt. and the install went smooth, and the os works great too, until it decides to reboot.  it doesn't have to be doing anything, the screen goes black, except for text that says log out on tty1, and prompts for login, and then it displays the xubuntu splash art, and shuts down properly, and powers its self off.  i'd appriciate any suggestions, as i had to reinstall winxp to make the pc useable, but i'd really like to reinstall ubuntu, and forget ms ever existed

---

### Post by newman on 2006-06-27
Check your system BIOS to see if CPU temp shutdown is enabled and disable it if it is.  I had a similar problem with suse linux - it was shutting down because it was reading the CPU temp from BIOS as too hot, even though it wasn't, and it would shut down after few minutes.

---

### Post by ghettohacker on 2006-06-27
thanks for the suggestion.  ther was no setting for cpu temp in my bios, but there was a setting to select OS type, and for options it had 'MSDOS' and 'other'.  so i selected other as a test.  im currently running xubuntu 6.06 from the LiveCD, and i'll let the pc idle for a while, and see if it shuts it's self down.  if not i'll install ubuntu again and see what happens.  thanks for the suggestion.

---

### Post by newman on 2006-06-27
I'm most certain there should be a section in the BIOS called "PC Health Status" or something similar, and that's where you'll find "Target Shutdown Temp."

---

### Post by ghettohacker on 2006-06-28
i looked for anything in the bios settings, but didn't find anything relative to your suggestion.  after installing from the livecd that worked perfectly, the install failed.  it crashed to a black screen twice, i dont recall where as i was out of the room each time.  today i installed ubuntu 5.10 and it also works perfectly.  any suggestions of what upgrades i should do on a new 5.10 install before upgrading it to dapper, if any?

---

