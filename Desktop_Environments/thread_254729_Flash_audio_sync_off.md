---
title: "Flash audio sync off"
date: 2006-09-10
forum: Desktop Environments
---

### Post by frequenicity on 2006-09-10
When playing Flash media in firefox the audio is still out of sync with the video despite using the alsa-oss and "aoss firefox" and "aoss" as the DSP.

I have read somewhere that a possible fix may be to allocate more memory/larger cache to flash? What is the method to do this? (in the about:config?) Or is there another fix?

---

### Post by spiregrain on 2006-09-10
If you visit this site:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html)

The flash plugin displays its global preferences settings.   I'm not sure if this will help.  The default is 100K, and after viewing a movie on YouTube,  I found that only 1K was used.

Let me know if it worked for you.

---

### Post by frequenicity on 2006-09-10
Increased to 1mb. Still out of sync. I'm sure other people have experienced this. Any known fixes? The videos start off in sync and then a little bit into them (15 seconds) its off by about a second or so.

---

### Post by Mike-Bell on 2006-09-15
Same problem, any idea?

---

### Post by frequenicity on 2006-09-15
Seems to me like its just going to have to wait until the flash 9 beta is released. I was able to wine firefox and flash 8.5 and it gets a little better..

---

### Post by Odinist on 2006-09-15
Close your browser, open a terminal, *sudo killall esd*, then open FF back up, see if the audio stays in sync this time.

---

### Post by verbatim on 2006-09-16
> sudo killall esd

This solution from the post above worked for me.

---

### Post by Odinist on 2006-09-16
^_^


That'll work too if you're watching movies with Totem and they're getting out of sync... Kill the ESD process, and the sound will stay in sync.

---

### Post by dmizer on 2006-09-17
this did not work for me:
```
~$ sudo killall esd
esd: no process killed

```
with no browser open, and gaim closed.

---

### Post by Odinist on 2006-09-18
> **dmizer said:**
> this did not work for me:
```
~$ sudo killall esd
esd: no process killed

```
with no browser open, and gaim closed.

Hrm...

Might wanna read through this thread:

[http://ubuntuforums.org/showthread.php?t=186594&highlight=flash+sound+sync]("http://ubuntuforums.org/showthread.php?t=186594&highlight=flash+sound+sync")

---

