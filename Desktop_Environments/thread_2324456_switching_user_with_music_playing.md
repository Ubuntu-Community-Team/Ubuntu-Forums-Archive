---
title: "switching user with music playing"
date: 2016-05-14
forum: Desktop Environments
---

### Post by Skaperen on 2016-05-14
i switch users in Unity, now under 16.04 LTS, often. i have different usernames for different purposes and for security isolation.  _i would like to have music playing continuously as i switch users._ starting the music play as root is an option.

---

### Post by mcduck on 2016-05-14
Maybe take a look at [Music Player Daemon]("https://www.musicpd.org/"), it's a music player that runs as a background service  as it's own user and can then be controlled with various different clients, including nice graphical ones, command-line client, and even web-based clients for remote control.

Because it runs as a daemon, it'll play back your music regardless of if you are logged in or not. (actually if you leave it playing when you shut down your computer, it will even resume from where it left before you even get a chance to log in yourself!)

It's been a while since I've used it, but it's pretty simple to set up, and at least Sonata was nice & lightweight client for it. You should find MPD in Ubuntu's repositories, probably Sonata as well...

---

### Post by Skaperen on 2016-05-28
i get this:> apt-get -y install music-player-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package music-player-daemon
FYI:
i have run my *play* script as a daemon even as root and the music stops as soon as i switch to another user.

---

### Post by Skaperen on 2016-06-24
*not working.*  when i switch user from where i started it playing, the music stops.  when i switch back it resumes.

---

### Post by mcduck on 2016-06-26
The package is called "mpd" (and you'll probably want to make sure you also install some client as well). You'll also need to configure it, and for this purpose make sure to set it up as a daemon, not for running it as your own user.

---

