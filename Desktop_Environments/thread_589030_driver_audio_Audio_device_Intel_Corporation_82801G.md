---
title: "driver audio Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud"
date: 2007-10-23
forum: Desktop Environments
---

### Post by mvitti01 on 2007-10-23
I installed ubuntu 7.10 and my lap doesnt' make any sound.

how can I install the driver ??? or any solution?

---

### Post by iClouseau88 on 2007-10-23
Hi,

This worked for me:

$asoundconf list

Take note of your sound card from the list of available cards, for example I82801BAICH2

$asoundconf set-default-card {I82801BAICH2, i.e. your soundcard}

Also: click on the speaker icon and "un-mute" all settings, and make sure volume levels are not the lowest.

:)

---

### Post by gui_love on 2007-10-24
try this

[http://ubuntuforums.org/showthread.php?t=567642](http://ubuntuforums.org/showthread.php?t=567642)

---

### Post by mvitti01 on 2007-10-29
thank you very much I'll try it and comment the result

---

### Post by mvitti01 on 2007-10-30
Nothing of your advices worked out... any other suggestion?

Thank u anyway

---

