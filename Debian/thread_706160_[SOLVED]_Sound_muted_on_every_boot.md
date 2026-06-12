---
title: "[SOLVED] Sound muted on every boot"
date: 2008-02-24
forum: Debian
---

### Post by benerivo on 2008-02-24
When i installed debian (unstable), my sound card (Creative Labs SB Audigy) was detected straight away and it works perfectly, only that the alsa mixer settings are never saved. By default, the main volume channel is set to 0 (mute), so i have to manually change it every time i boot the computer. I have looked at these solutions but neither work...

[URL="http://www.debianhelp.co.uk/sound.htm"]Append these lines to your /etc/rc.d/rc.local or /etc/init.d/alsasound 
/usr/bin/amixer set Master 50 unmute >/dev/null 2>&1 
/usr/bin/amixer set PCM 50 unmute >/dev/null 2>&1 
/dev/null /usr/bin/amixer set CD 50 unmute >/dev/null 2>&1[/URL]

[http://ubuntuforums.org/showthread.php?t=547642](http://ubuntuforums.org/showthread.php?t=547642)
[http://ubuntuforums.org/showthread.php?t=189055](http://ubuntuforums.org/showthread.php?t=189055)

I should mention that these solutions suggest altering files that are not present on my setup (ie. /etc/init.d/alsasound) so i had to create them. I'm guessing my solution might be that i need to save/modify my alsa sound settings elsewhere.

Thanks

EDIT - This was solved by installing alsa-utils and alsa-base.

---

