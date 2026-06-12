---
title: "where is alsamixer?"
date: 2006-01-07
forum: Desktop Environments
---

### Post by ryan76 on 2006-01-07
I'm up to step 18978294 in configuring my sound and everything keeps saying 'check in alsamixer...'

but I get this:
```

ryan@ubuntu:~$ alsamixer
bash: alsamixer: command not found
```

It's not in synaptic either. gnome-alsamixer gives a blank dialog box then quits 'unexpectedly'.

I've installed the drivers and so forth but no sound card is detected in System > Preferences > sound.

Can someone tell me where to get the elusive alsamixer from?

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=ryan76]I'm up to step 18978294 in configuring my sound and everything keeps saying 'check in alsamixer...'

but I get this:
```

ryan@ubuntu:~$ alsamixer
bash: alsamixer: command not found
```

It's not in synaptic either. gnome-alsamixer gives a blank dialog box then quits 'unexpectedly'.

I've installed the drivers and so forth but no sound card is detected in System > Preferences > sound.

Can someone tell me where to get the elusive alsamixer from?[/QUOTE]
It is part of the alsa-utlis package.

---

### Post by ryan76 on 2006-01-07
Thanks, I have that installed already. I reinstalled it anyway. Now I get:

ryan@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

---

