---
title: "enormous .xsession-errors, GNOME in some sort of debug mode ..."
date: 2011-04-16
forum: Desktop Environments
---

### Post by kelt65 on 2011-04-16
My maverick (10.10) desktop is acting extremely sluggish and creating a huge .xsession-errors file (25GB after a couple of days) full of messages such as the following:

```
(gnome-session:7505): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus
```

It looks like gnome-session is in some sort of debug mode. Linking .xsession-errors to /dev/null will keep the file from filling up my disk but of course does nothing to solve the sluggishness (except that writing to /dev/null might be a little faster than to disk). Does anyone know how this happened? ps -ef does not show that gnome-session has the --debug flag. Please tell me this isn't hard coded in ...
As it stands, my desktop is now unusable for what I use it for, photo and video editing (and this is an 2.4GHz dual core with 16GB of memory). Web surfing is tolerable, but if this was a bug introduced by an update (and it does appear that way), this is seriously terrible.

---

