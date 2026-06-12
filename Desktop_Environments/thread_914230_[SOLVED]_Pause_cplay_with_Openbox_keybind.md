---
title: "[SOLVED] Pause cplay with Openbox keybind"
date: 2008-09-08
forum: Desktop Environments
---

### Post by FakeOutdoorsman on 2008-09-08
When I previously used Gnome with Quod Libet I could create a hotkey that would run the "quodlibet --pause" command.  cplay doesn't have a pause command that I know of, so I have to manually bring up the terminal and then press "z", which pauses cplay.  I would rather just use a hotkey or keybind in Openbox to pause cplay.  How can I do this?

---

### Post by urukrama on 2008-09-08
I'm not sure it is possible, unless one of the apps cplay uses (such as mpg123 or mpg321) support it.

Why don't you use mpd with ncmpc? You can easily control mpd on the command line with mpc. I know it can be annoying if you want to play files that are not in your database, but otherwise mpd is great.

---

### Post by FakeOutdoorsman on 2008-09-08
Thanks for the quick reply.  Is there a way to keybind to focus a particular window if it is in the background without having to alt+tab or middleclick?  If not, then I suppose I'll dump cplay.  I installed mpd and ncmpcpp eariler today, but thought I would give cplay one more chance since I like its databaseless simplicity.

---

### Post by urukrama on 2008-09-08
You could modify [this script I talked about on my blog]("http://urukrama.wordpress.com/2008/05/05/focus-an-application-instead-of-re-launching-it/") and bind that to a keybind in Openbox. You'll need wmctrl installed for that.

---

### Post by FakeOutdoorsman on 2008-09-08
Thanks.  It worked just fine.  I really should keep up with your blog.

---

