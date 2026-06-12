---
title: "Creating a &quot;Cloud&quot; Desktop"
date: 2011-05-02
forum: Desktop Environments
---

### Post by OldTimeyJunk on 2011-05-02
Basically, I've created a simple GDM Entry for a Cloud desktop which runs Chromium...

[Desktop Entry]
Encoding=UTF-8
Name=Cloud
Comment=
Exec=/usr/bin/chromium-browser
Icon=
Type=Application

It works perfectly but the only problem is the window doesn't fill the whole screen, just part of the screen (sort of like when you open the XTERM environment). Is there any variables I can stick onto the end of the command or do I need to edit "chromium-browser".

I have tried the "--maximized" command on the end (I don't even know if that's a real command).

How can I make it so that Chromium fills the whole screen, any suggestions?

BTW: I have the "Use System title bar and borders" checked so it doesn't show the Minimize/Maximize/Close buttons so don't just tell me to press "Maximise" everytime...

---

### Post by BrokenKingpin on 2011-05-02
Try it with the --start-maximized. There should also be one for a full screen mode.

See this link for more command line switches:
[http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/)

---

