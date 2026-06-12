---
title: "How to open a folder on login?"
date: 2010-07-21
forum: Desktop Environments
---

### Post by freemant on 2010-07-21
Hi,

I'd like to open a folder automatically after logging in. The folder is a samba shared folder but it shouldn't matter. I've tried launching nautilus as a "startup application", but then Ubuntu will enter some kind of loop and pop up lots of window saying "starting file manager".

Any idea to achieve that? I am using Ubuntu 10.04.

Thanks!

---

### Post by munkyeetr on 2010-07-21
This may help you: [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

---

### Post by freemant on 2010-07-21
Thanks! I tried using the following as .xinitrc but it isn't working:

#!/usr/bin/env bash
netuse.sh &
exec gnome-session

where netuse.sh will launch nautilus to open the folder.

Any idea?

---

### Post by freemant on 2010-07-21
In fact, it seems that the .xinitrc and .xsession files are ignored by gnome.

---

