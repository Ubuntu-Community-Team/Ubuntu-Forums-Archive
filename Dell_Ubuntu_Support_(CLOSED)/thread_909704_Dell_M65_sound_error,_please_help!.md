---
title: "Dell M65 sound error, please help!"
date: 2008-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dkhajavi on 2008-09-03
This is my first post!  I have actually been doing pretty well being a lifetime Microslow user!  But I have hit a wall with sound issues.  I think this is different from other users I have read about in the forums.  Here is what I have:
Dell M65 (originally XP Pro) 
Ubuntu 8.04 
Kernal 2.6.24-19-server
Gnome 2.22.3
2 GiB
Processor 0 - Intel Core T7400 @ 2.16GHz
Processor 1 - Intel Core T7400 @ 2.16GHz

I understand it is a Sigmatel Sound card.

When I first installed Ubuntu I had sound and all was well.  I did not have the nvidia drivers working well.  I went around installing various items from the repository to get everything working.  Once I had everything done I noticed I had no sound.  I saw a muted speaker icon on the top navigating bar and went to un-mute it but instead got the following error message 'No volume control GStreamer plugins and/or devices found.'.  I have also tried to use things like VOIP phones, audio player and other applications needing sound and I get errors like 'no audio devices found'.  

This seems to be the last 'issue' clouding up an otherwise great experience switching!  Can you help?

---

### Post by dkhajavi on 2008-09-04
One more piece of info:

When I boot into an earlier install version 16 Generic I get sound (had video issues though), when I load the latest version in my system version 19 Server, I get great everything but just no sound and the error message.

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lspci
```

---

