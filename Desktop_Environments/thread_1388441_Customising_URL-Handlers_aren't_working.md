---
title: "Customising URL-Handlers aren't working"
date: 2010-01-23
forum: Desktop Environments
---

### Post by DigitalRanger on 2010-01-23
Hello,
I've just switched to using Chromium in Karmic (Ubuntu 9.10), and I'm trying to use gconf-editor to change two URL-Handlers - _without_ success!

**[SIZE="4"]First: Default HTTP/S handlers[/SIZE]**
I have used Chromium's own settings to make it the default browser. However, if I create a web launcher on my desktop, double-clicking it still launches Firefox. I've tried changing the *http* and *https* url-handlers to *chromium-browser* rather than *Firefox*. I currently have both set-up in gconf-editor as:

/desktop/gnome/url-handlers/http
[LIST]
[*]command: chromium-browser "%s"
[*]enabled: true
[*]needs_terminal: false
[/LIST]

/desktop/gnome/url-handlers/https
[LIST]
[*]command: chromium-browser "%s"
[*]enabled: true
[*]needs_terminal: false
[/LIST]

_However, desktop launchers to websites still launch Firefox!_

**[SIZE="4"]Second: Spotify Handler[/SIZE]**
Since Chromium doesn't have the same comprehensive application association set-up that Firefox does, I tried setting up a general Spotify url-handler in GNOME. I've set up the following on my gconf-editor:

/desktop/gnome/url-handler/spotify
[LIST]
[*]command: /home/digitalranger/.browser2spotify.sh "%s"
[*]enabled: true
[*]needs_terminal: false
[/LIST]

Where browser2spotify.sh is a script with the following content
```
#!/bin/sh
exec wine "C:\Program Files\Spotify\spotify.exe" /uri "$@"
```

_Despite having done this, nothing happens when I click Spotify links in Chromium._

---

### Post by user1397 on 2010-01-23
have you tried simply logging out/back in after making said changes?

---

### Post by DigitalRanger on 2010-01-23
> **ubuntuman001 said:**
> have you tried simply logging out/back in after making said changes?

Hi, yes I've completely rebooted several times, thanks.

---

### Post by DigitalRanger on 2010-01-25
It seems the HTTP/S handlers are actually okay, it's just when you try to run a desktop launcher such as

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Link
Icon[en_GB]=gnome-panel-launcher
URL=http://www.allaboutsymbian.com/features/item/Battle_of_the_Maps-Revisited.php
Name[en_GB]=Battle of the Maps - Revisited
Name=Battle of the Maps

``` 

Then Firefox loads, but I've also been told this happens in Fedora, so it's a GNOME issue.

Where as if I go to the terminal and type
```
gnome-open http://www.google.com
```
Then Chromium launches.

The Spotify issue was a syntax problem.
```
command: /home/digitalranger/.browser2spotify.sh "%s"
```
Needed to be
```
command: /home/digitalranger/./browser2spotify.sh "%s"
```

---

