---
title: "Logout script"
date: 2010-02-06
forum: Desktop Environments
---

### Post by coticj on 2010-02-06
Hello,

I'm using a special screensaver, thar runs the a script. I've called the script logout.

It looks like this:

#! /bin/bash
# Logout komanda
gnome-session-save --kill --silent
rm -rf /home/start
cp -R /usr/share/start /home
chown -R start:start /home/start

The gnome-session command works, and I'm loged out immideately. So does the rm -rf. But the cp doesn't. I've tried setting the permissions on /home to 777, but it still doesn't work. When i run the script as another user it copies that. Otherwise it doesn't. Any clue to what might be wrong?

---

