---
title: "Rhythmbox crashes"
date: 2005-11-22
forum: Desktop Environments
---

### Post by Bou on 2005-11-22
That's right, when I try to listen to an online redio station (example:[http://www.ondacero.es/europafm.asx](http://www.ondacero.es/europafm.asx)) Rhythmbox crashes. Other players like Totem can handle them, though. I would like to know if this happens to you too, and if there's any way to fix it.

Thank you.

---

### Post by doclivingston on 2005-11-23
When trying to play that, I get several warnings on the console ```
Entity: line 7: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xA9 0x20 0x4F 0x6E
    <Copyright>\uffff Onda Cero 2004</Copyright>
``` and then it hangs inside gstreamer. Are you using Totem-gstreamer or Totem-xine? because totem-gstreamer hangs for me too (because the problem is in gstreamer).

I would file a bug ([http://bugzilla.ubuntu.com)](http://bugzilla.ubuntu.com)), against gstreamer.

---

### Post by Bou on 2005-11-23
I am using Totem-xine, guess you're right. I'll fill the bug.

Thanks a lot!

---

### Post by Burning Bronx on 2005-11-23
GStreamer is pretty messed up here too (I mean it was in Breezy as I haven't bothered to test on Dapper). That's why I use Totem-xine or VLC (best movie player IMO) and Beep Music Player for music (all available on Universe repositories).

---

### Post by doclivingston on 2005-11-23
Now that I look closer at the hang, it might actually be libmms (which gstreamer uses). In any case, the bug will get passed around to whoever needs to fix it.

---

