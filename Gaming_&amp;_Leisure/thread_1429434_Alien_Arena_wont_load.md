---
title: "Alien Arena wont load"
date: 2010-03-14
forum: Gaming &amp; Leisure
---

### Post by leinad177 on 2010-03-14
when i try to load up the game by clicking on it in the menu, nothing happens

i downloaded it in the software center and im running 9.10

thanks in advance

---

### Post by Toffeeapple on 2010-03-14
Run it from a terminal and see what error message is given. I think the command is 'alienarena' but I may be wrong.

---

### Post by leinad177 on 2010-03-14
> **Toffeeapple said:**
> Run it from a terminal and see what error message is given. I think the command is 'alienarena' but I may be wrong.


how do i do that?

---

### Post by Enigmapond on 2010-03-14
Open a terminal and type...

```
alienarena or alien-arena
```

---

### Post by leinad177 on 2010-03-14
```
daniel@daniel-desktop:~$ alien-arena
using /home/daniel/.alien-arena/data1/ for writing
using /home/daniel/.alien-arena/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
```

---

### Post by leinad177 on 2010-03-14
bump

---

### Post by Toffeeapple on 2010-03-14
A quick google of your error message..

```
bt_audio_service_open: connect() failed: Connection refused (111)
```

..and I found this..
> It seems that the pulseaudio backend of openal is broken in karmic.
So sound for alien-arena won't work in karmic :-(
..[here]("https://bugs.launchpad.net/getdeb.net/+bug/480928").

---

