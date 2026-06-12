---
title: "Using PostSession scripts"
date: 2008-10-27
forum: Desktop Environments
---

### Post by Shardsofmetal on 2008-10-27
The first thing I need to know, are PostSession scripts, like /etc/gdm/PostSession/Default, executed before the screen goes black, or right after? I ask because I've added 3 lines to the file
```
dcop amarok playlist saveCurrentPlaylist
dcop amarok player stop
sleep 3.6
```above the "exit 0" command, yet they aren't being run before gnome exits. The point of the commands is to save the current playlist before exiting everything, and to fade out the music like in kde, without my having to manually exit the program. Am I doing something wrong, or should this work?

---

### Post by lswb on 2008-10-27
When /etc/gdm/PostSession/Default runs, the user has already logged out of gnome and the X server for that session has or will shortly shut down as well. What's more the Default script is running as root, not as user. It does set $USER to be the name of the user who logged out if that helps you, but it's not really designed to be a user logout script in the sense that .bash_logout is for a bash login shell. Unfortunately there is no ready-made script that runs as the user on gnome logout. Here's some information from gnome.org:

[http://library.gnome.org/admin/gdm/stable/index.html.en](http://library.gnome.org/admin/gdm/stable/index.html.en)
and
[http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en)

But you'll probably have to google a little deeper to get all the gory details. I wish there was someplace in the gnome configuration to drop commands like you want and have them execute at logout.

---

