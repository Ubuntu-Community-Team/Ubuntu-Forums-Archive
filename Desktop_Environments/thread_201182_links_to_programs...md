---
title: "links to programs.."
date: 2006-06-21
forum: Desktop Environments
---

### Post by Jawbreaker4Fs on 2006-06-21
Can anyone refresh my memory as to how to make a sort of link for an application. I want to run uTorrent through wine by just typing "utorrent" at a terminal. The location is /opt/uTorrent/utorrent.exe. I did this before I formatted by having some small bash scripts in /usr/bin/, but I can't remember the exact syntax for doing this. Any help would be appreciated. Thanks!

---

### Post by bluevoodoo1 on 2006-06-21
hmmm I've never used uTorrent... how about this...

```
sudo gedit /usr/bin/startutorrent
```

```

#!/bin/sh

wine /opt/uTorrent/utorrent.exe
```

```
sudo chmod +x /usr/bin/startutorrent
```

Edit: if "utorrent" isn't used by another program, you could rename "startutorrent" to "utorrent" and it'll open by typing "utorrent"

---

### Post by Ramses de Norre on 2006-06-21
Copy this to a file /usr/bin/utorrent ```
#!/bin/bash
wine "/opt/uTorrent/"utorrent.exe

```
Then do ```
sudo chmod +x /usr/bin/utorrent
```
And you'd be fine ;)

---

### Post by Jawbreaker4Fs on 2006-06-21
Thanks guys! Just what I was looking for.

---

