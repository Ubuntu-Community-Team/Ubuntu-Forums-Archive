---
title: "Nautilus is opaque occupying screen"
date: 2018-02-23
forum: Desktop Environments
---

### Post by jtodd.fr on 2018-02-23
I switch to i3 wm a while ago, and configure most of stuffs that now are working without a problem. But when I started to launch nautilus file manager, I notice it instead of displaying files, folders layout as usual (as in Unity desktop env). Now it becomes opaque, shown like [https://imgur.com/a/HbeE4](https://imgur.com/a/HbeE4), occupying my screen (left hand side color that looks like unity 16.04 LTS wallpaper). Are there log files I can check or any way I can debug this?

Thanks

---

### Post by vanadium on 2018-02-23
You mean tranparant rather than opaque - in other words, the window does not appear. Close that window and launch nautilus from a terminal: this will show error messages that may help more. Are you using a windows compositor (typically compton)? You might need to adjust its settings. Try whether the issue also occurs without compton - this will immediately indicate whether compton is the problem or not.

---

### Post by jtodd.fr on 2018-02-26
No. It's opaque because once nautilus is launched, it blocks the view behind it, including the terminal (in another screen, which is completely blocked by Ubuntu wallpaper like decoration. [I use dual monitor]) that launches the nautilus. It just happens nautilus appearing the same decoration as Ubuntu wallpaper. 

I manage to write message to file, which only has following output content. 

```

(nautilus:13330): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (nautilus:13330): WARNING **: Can not get _NET_WORKAREA


** (nautilus:13330): WARNING **: Can not determine workarea, guessing at layout

```

Not sure if the system runs with composite manager, but search by command `ps -ef | grep compo | grep -v chromium-browser` shows no composite manager is running. 
```

userA     15353 15255  0 10:42 pts/0    00:00:00 grep --color=auto compo

```

Checking with `ps -ef | grep comp | grep -v chromium-browser` shows
```

root        63     2  0 Feb23 ?        00:00:00 [kcompactd0]
userA      3355     1  0 Feb23 ?        00:00:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.2 /org/gtk/gvfs/exec_spaw/6

```

Try with command `sudo apt-get install compton` noticing compton is not stilled in fact.
```

The following NEW packages will be installed:
  compton libconfig9
0 upgraded, 2 newly installed, 0 to remove and 49 not upgraded.
Need to get 123 kB of archives.
After this operation, 328 kB of additional disk space will be used.
Do you want to continue? [Y/n] ^C 

```

Searching /var/log/Xorg.0.log doesn't find any EE (error) messages. /var/log/syslog doesn't find error as well.

---

### Post by jtodd.fr on 2018-02-26
Came across to this thread - [https://ubuntuforums.org/archive/index.php/t-956120.html](https://ubuntuforums.org/archive/index.php/t-956120.html)

It looks like in default nautilus will manage the desktop as well (where log messages show it [COLOR=#000000][FONT=&amp]Can not get _NET_WORKAREA ... [/FONT][/COLOR][COLOR=#000000][FONT=&amp]Can not determine workarea, gussing layout[/FONT][/COLOR]  ). So passing argument --nodesktop telling nautilus not to manage desktop do the trick. 

```

nautilus --no-desktop

```

Not sure if this is the right solution or not, but at least it solves my current issue.

---

