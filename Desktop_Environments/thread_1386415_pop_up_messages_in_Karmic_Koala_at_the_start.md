---
title: "pop up messages in Karmic Koala at the start"
date: 2010-01-20
forum: Desktop Environments
---

### Post by Adsg on 2010-01-20
Hi
Since Kermic, at the start of my session, on the right of my screen I can see a message that pops up to tell me the wireless connection has been done or has been lost.

[IMG]http://img191.imageshack.us/img191/6238/popupmessage.png[/IMG]

This pop up is really cool because when you put the cursor on it, the message disappears so that you can't click on it. And if you remove your cursor from the place, the message appears again.

I would like to be able to send such messages to myself. Do you know how please ?

---

### Post by sisco311 on 2010-01-20
You can use notify-send:

```
notify-send -i path/to/icon.png "Title" "Message Text"
```

---

### Post by stinkeye on 2010-01-20
You can even play an audio file  at the same time.
eg I use this script with my gmail conky
```
#!/bin/bash

notify-send --icon=/home/glen/Pictures/gmail2.png "Gmail" "You have new mail" &
play -q ~/Sounds/message.wav
```

You need to install sox for the play command to work and I think
it only works with wav files.
```
sudo apt-get install sox
```

---

### Post by Adsg on 2010-01-21
Thank you so much sisco311. This works perfectly :D   Thank you stinkeye too!! The trick about the sound is very cool ^_^    In love with ubuntu

---

