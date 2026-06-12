---
title: "How to remove everpad lense from unity dash home view?"
date: 2014-02-20
forum: Desktop Environments
---

### Post by Oh_SeungHwan on 2014-02-20
[INDENT] 					I have used 13.04 version.

I have installed everpad 2.5.7 (I know it is the latest version.)

After it did, everpad lens' items to be displayed on Dash home.

I wanted to remove that on Dash home.

And I unchecked "Everpad appindicator-->Settings and Management-->Appearance-->Search on the home lens" option.

Yet it is being displayed.

And I removed everpad package by "sudo apt-get remove", "sudo apt-get purge" command.

Everpad lens' item disappeared. But as I reinstall everpad, it appears again.

So I tried to use Unity Tweak, dconf-editor but they didn't help me to remove it.

How can I remove it on Dash home? 				[/INDENT]

---

### Post by sinan5 on 2014-10-30
"sudo apt-get autoremove everpad" did the trick for me.

---

