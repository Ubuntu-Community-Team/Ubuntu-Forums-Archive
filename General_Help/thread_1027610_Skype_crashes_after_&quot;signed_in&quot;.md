---
title: "Skype crashes after &quot;signed in&quot;"
date: 2009-01-01
forum: General Help
---

### Post by gingaz on 2009-01-01
Hello,

i have a problem - skype won't start. Don't remember doing something with configs, especially with skype.

When i run skype in terminal everything is OK and after "signed in" screen skype just closes. Here's the text from terminal:

~$ skype
ALSA lib pcm_bluetooth.c:1619: (bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619: (bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
Aborted


Any ideas how to fix it? And what bluetooth has to do with skype? I don't use it.

PS. Maybe you know where Skype is keeping it's settings? I would like to reset them, because now, even completely removed and then reinstalled, it remembers my login and option to automatically connect.

Thank you!

---

### Post by gingaz on 2009-01-02
Ahh, OK, found .Skype directory (searched for .skype)...

Deleted whole directory ant all went fine.

---

