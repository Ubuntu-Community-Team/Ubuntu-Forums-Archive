---
title: "Shell script on startup"
date: 2007-06-22
forum: Desktop Environments
---

### Post by SteinbergerNate on 2007-06-22
Is there any way to get a shell script to start when I login? I've been trying through the System/Preferences/Sessions menu selection but I just can't get it to work. I just need it so I can run sunrise desktop on startup.

---

### Post by lixy on 2007-06-22
sudo chown -R [uname] ~/.config/autostart

That oughta fix it.

---

