---
title: "Desktop and home folder the same?"
date: 2009-01-15
forum: General Help
---

### Post by Elusid on 2009-01-15
So I came across a strange problem when I installed Ubuntu 8.10 on my laptop yesterday. It seems that my Desktop is also now my home folder which works but now I have folders everywhere on my desktop. I've installed Ubuntu several times before on other computers and it hasn't done that. Any ideas what's going on?

---

### Post by taurus on 2009-01-15
Did you somehow create a shortcut to your $HOME on your desktop?  What is the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by redilyn on 2009-01-15
This applys to eeebuntu but should work for ubuntu too.

Create any directories you may be missing

```

cd ~/
mkdir Desktop Downloads Templates Public Documents Music Pictures Videos

```

Configure the system to use those directories

```

gedit ~/.config/user-dirs.dirs

```

Change the following

```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

Save the file, then logout and login. You should be good to go

---

### Post by Elusid on 2009-01-15
> **redilyn said:**
> This applys to eeebuntu but should work for ubuntu too.

Create any directories you may be missing

```

cd ~/
mkdir Desktop Downloads Templates Public Documents Music Pictures Videos

```

Configure the system to use those directories

```

gedit ~/.config/user-dirs.dirs

```

Change the following

```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

Save the file, then logout and login. You should be good to go

Ha that worked, thanks =)

---

