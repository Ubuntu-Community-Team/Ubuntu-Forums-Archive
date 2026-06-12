---
title: "Autostart programs in iceWM"
date: 2009-01-19
forum: Desktop Environments
---

### Post by jerome1232 on 2009-01-19
Hello I've recently started using iceWM as my main window manager. I can't seem to get a few things I need to auto start.

I'm using pcmanfm for my filemanager, and it's handling drawing my desktop, I also need nm-applet to startup.

According to icewm docs I just place a script at ~/.icewm/startup, I tried this and it's not working for me, neither program get's autostarted and I end up with an open xterm that refuses to close, I can't log out without restarting x.

Here is the content's of the script at ~/.icewm/startup, yes I did remember to make it executable.

```
#!/bin/sh
pcmanfm&
nm-applet&
```

Any help would be appreciated!

---

### Post by jerome1232 on 2009-01-20
I think I actually solved this, I just had to add a sleep in between commands.

So in short the script should look like this
```
#!/bin/bash
programstorun&
sleep 1
programtorun&
```

---SOLVED---

---

