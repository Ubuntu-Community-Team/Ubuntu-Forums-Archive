---
title: "Spotify with terminal or SSH"
date: 2015-01-28
forum: Desktop Environments
---

### Post by themedserv2 on 2015-01-28
HI I have a strange behavior here.

I don't know if it is Ubuntu or Spotify, but some reports spotify works well under my setup..

If I launch spotify via Ubuntu gnome-terminal like so
```
spotify
```
Spotify launches well..


```
whoami
```
And the user who launch it, is let say user01:


But in the same terminal if I use this command:
```

sudo su user01 -c spotify

```

It throws this error:
[COLOR=#555555][FONT=Arial]ERROR: Spotify is already running, but not responding. Please close it and try it again

[/FONT][/COLOR]I want to launch spotify via another application (irexec) but I can't run in any other way then via the gnome-terminal..

It runs well under root tho:
```
sudo su root -c spotify
```


Open Spotify via SSH work only with root:
```
sudo su
export DISPLAY=:0
spotify
```

But i don't want to run it under root..

Any ideas?
Thks!

---

