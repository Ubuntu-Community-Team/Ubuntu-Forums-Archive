---
title: "unity: &quot;There was an error launching the application&quot;"
date: 2013-01-14
forum: Desktop Environments
---

### Post by alec.leamas on 2013-01-14
I have a .desktop file which gives the message above when trying to run it. The file:
```

[Desktop Entry]
Name=My Spotify
GenericName=Music Player
Comment=Listen to music using Spotify
Icon=spotify-client
Exec=/home/al/bin/my-spotify
TryExec=/home/al/bin/my-spotify
Terminal=false
Type=Application
Categories=Qt;Audio;Music;Player;AudioVideo;Education;
MimeType=x-scheme-handler/spotify;

```
I'm really trying to make this a personal thing and stores it in ~/.local/share/applications. But storing in /usr/share/applications gives same result. I have
[LIST]
[*]Used it successfully on other distributions/desktops.
[*]Tested on a clean, virtual desktop install of 12.10.
[*]Logged out-in to reset unity.
[*]Set 755 permissions on the file.
[*]Run the script my-spotify from the command line, n p.
[*]Pasted some "set -x; exec &>/tmp/foo into  my-spotify for logging. This logs all commands into /tmp/foo. However, the log file is not even created.

[/LIST]

My conclusion is that unity refuses to even invoke my otherwise working wrapper my-spotify. But why? Are there logs somewhere? 

"leamas scratches his head"

---

### Post by zombifier25 on 2013-01-14
Launch the application from a terminal. The error messages that it gives can help diagnose the problem.

---

