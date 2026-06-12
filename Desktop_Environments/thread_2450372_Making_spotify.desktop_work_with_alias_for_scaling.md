---
title: "Making spotify.desktop work with alias for scaling?"
date: 2020-09-12
forum: Desktop Environments
---

### Post by Dáire Fagan on 2020-09-12
I have installed Spotify on Ubuntu 20.04.01 with apt from the Spotify repo as that is my preferred method of install. Unfortunately on my 3200 x 1800 the user interface is very small.

In ~./bash_aliases I have added the following line:

```
alias spotify='/usr/bin/spotify --force-device-scale-factor=2.0'
```

and in terminal I input:

```
. .bash.rc
```

For good measure, I have also rebooted.

If I enter the command spotify in terminal it is now scaled properly but when I open Spotify using the Gnome icon it is the same as before.

/usr/share/applications/spotify.desktop has a line ```
Exec=spotify %U
``` and if I run this from terminal scaling is also fixed.

How can I make it so the .desktop launch option uses the scaling I have set please?

---

### Post by CatKiller on 2020-09-12
Have you tried just sticking that additional configuration flag into your desktop file?

```
Exec=spotify --force-device-scale-factor=2.0 %U
```

---

### Post by Dáire Fagan on 2020-09-12
> **CatKiller said:**
> Have you tried just sticking that additional configuration flag into your desktop file?

```
Exec=spotify --force-device-scale-factor=2.0 %U
```

I should have explained, I plan to sync my .bashrc and config files across systems so I am trying to keep any custom settings contained within. As such I have purposely not just edited the Exec line.

Is there a workaround?

---

### Post by Holger_Gehrke on 2020-09-12
Not really. Aliases are substituted by the shell (bash, probably). There's no shell involved when calling programs through a .desktop file. You could put the changed .desktop file for spotify in $HOME/.local/share/applications - the directory for user-specific .desktop files - and add that directory to the ones you keep in sync.

Holger

---

### Post by Dáire Fagan on 2020-09-12
> **Holger_Gehrke said:**
> Not really. Aliases are substituted by the shell (bash, probably). There's no shell involved when calling programs through a .desktop file. You could put the changed .desktop file for spotify in $HOME/.local/share/applications - the directory for user-specific .desktop files - and add that directory to the ones you keep in sync.

Holger

Sounds good.

After moving the spotify.desktop file I can see in Nautilus there is a lock on the icon but I have edited the exec line from spotify %U to:

```
Exec=/usr/bin/spotify --force-device-scale-factor=2.0 %U
```

Is it correct for the URL parameter to come  at the very end there or should it be directly after /usr/bin/spotify?

I am looking at a permissions cheatsheet here but I am unsure if I should duplicate the permissions for jetbrains or for telegram?

```
user@host:~/.local/share/applications$ lltotal 20
drwx------ 1 user user 224 Sep 12 20:12 ./
drwxr-xr-x 1 user user 452 Sep 12 20:14 ../
-rwxrw-r-- 1 user user 353 Sep 12 12:42 jetbrains-idea.desktop*
-rwxrw-r-- 1 user user 440 Sep 12 12:40 jetbrains-toolbox.desktop*
-rw-rw-r-- 1 user user   0 Sep 11 18:58 mimeapps.list
-rw-rw-r-- 1 user user  58 Sep 12 11:28 mimeinfo.cache
-rw-r--r-- 1 root  root  238 Sep 12 09:47 spotify.desktop
-rw-rw-r-- 1 user user 411 Sep 12 11:28 telegramdesktop.desktop
```

---

### Post by Holger_Gehrke on 2020-09-14
The lock-icon in Nautilus is there because the file is owned by root. You could change ownership of the file - you really should not have files owned by root in your home directory - by running 'sudo chown user:user ~/.local/share/applications/spotify.desktop'.
The normal order is options first then parameters, but that's mostly convention. What order the 'spotify' program expects I can't tell you, but there might be some documentation. Try 'man spotify'.
The permissions on the file are the minimum that will work. Having the executable bit for the owner set would allow you to start the program from Nautilus with a double-click on the file. Making it writeable for the group does not make sense under the circumstances. I'd leave it as it is.

Holger

---

