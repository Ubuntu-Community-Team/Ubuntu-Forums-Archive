---
title: "getting vnc to start at boot up"
date: 2021-10-15
forum: Desktop Environments
---

### Post by maurice-volaski on 2021-10-15
I have the following code being executed from a systemd service file

```
[COLOR=#000000][FONT=Menlo]export DISPLAY=:1
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]/usr/bin/x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /home/maurice/.vnc/passwd -rfbport 5900 -shared[/FONT][/COLOR]
```

At startup it yields the following complaint:

```
[COLOR=#000000][FONT=Menlo]Oct 15 00:04:22 u20 vnc[2985]: xauth:[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]unable to generate an authority file name[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]Oct 15 00:04:22 u20 vnc[2940]: 15/10/2021 00:04:22 -auth guess: failed for display=':1'[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Oct 15 00:04:22 u20 vnc[2940]: 15/10/2021 00:04:22 -auth guess: since we are root, retrying with FD_XDM=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Oct 15 00:04:22 u20 vnc[2940]: 15/10/2021 00:04:22 -auth guess: failed for display=':1'[/FONT][/COLOR]
```

What exactly is wrong here? The command seems to be running, but, of course, I cannot connect.

---

### Post by maurice-volaski on 2021-10-15
The line
```
[COLOR=#000000][FONT=Menlo]export DISPLAY=:1[/FONT][/COLOR]
```

should read 

```
[COLOR=#000000][FONT=Menlo]export DISPLAY=:0[/FONT][/COLOR]
```

---

### Post by ActionParsnip on 2021-10-15
What are you doing on the remote system? There may be a sleeker solution to do what you require.....

---

