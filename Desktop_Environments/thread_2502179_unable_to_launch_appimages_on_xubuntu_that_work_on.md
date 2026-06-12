---
title: "unable to launch appimages on xubuntu that work on gnome"
date: 2024-11-04
forum: Desktop Environments
---

### Post by com-c on 2024-11-04
Hello
I have a problem launching my appimages on xfce/xubuntu desktops


libfuse2 is installed, the appimages files are executable. When I run the files, nothing launches.


What perplexes me is that if I launch gnome, everything works perfectly.


I am on a freshly installed and update Ubuntu 24.04.1 LTS, xfce/xubuntu was installed using the xubuntu-desktop package (and its dependencies).

---

### Post by 1fallen on 2024-11-04
All mine work with "fuse3"
NOTE:
```
apt policy libfuse2 
libfuse2:
  Installed: (none)
  Candidate: (none)
  Version table:

```

---

### Post by Dennis N on 2024-11-04
> libfuse2 is installed, the appimages files are executable. When I run the files, nothing launches.

Try to start the appimage from the terminal. An error message may tell you what library is missing. Then search for the missing library in [Ubuntu Package Search]("https://packages.ubuntu.com/") in the "Search the contents of packages" section to find the package containing the library and install it.

Example of error message:
> error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory

---

### Post by com-c on 2024-11-04
[COLOR=#333333][FONT=Verdana]Thank you for your interest
[/FONT][/COLOR][COLOR=#333333][FONT=Verdana]

[/FONT][/COLOR]

---

### Post by com-c on 2024-11-04
> **1fallen2 said:**
> All mine work with "fuse3"
NOTE:
```
apt policy libfuse2 
libfuse2:
  Installed: (none)
  Candidate: (none)
  Version table:

```

if I run apt policy libfuse2 in a terminal, I have the same result as you
```
  Installed: (none)
  Candidate: (none)
  Version table:
```

---

### Post by com-c on 2024-11-04
> **Dennis N said:**
> Try to start the appimage from the terminal. An error message may tell you what library is missing. Then search for the missing library in [Ubuntu Package Search]("https://packages.ubuntu.com/") in the "Search the contents of packages" section to find the package containing the library and install it.

Example of error message:


Thank you for your interest


when i run it in a terminal
> [11621:1105/005050.041984:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /tmp/.mount_LM_StuwS29T2/chrome-sandbox is owned by root and has mode 4755.
Trappe pour point d'arrêt et de trace (core dumped)

> sudo chmod 4755 /tmp/.mount_LM_StuwS29T2/chrome-sandbox[sudo] Captain password:
chmod: cannot access '/tmp/.mount_LM_StuwS29T2/chrome-sandbox': No such file or directory

---

### Post by 1fallen on 2024-11-05
Some Appimages need "elevation" to run (sudo) but it would ideal if it prompted for the root password first.

What appimage is it?



The normal settings for /tmp are 1777 aka "a=rwx,o+t", which ls shows as drwxrwxrwt.(see my code box) That is: wide open, except that only the owner of a file (or of /tmp, but in that case that's root which has every right anyway) can remove or rename it (that's what this extra t bit means for a directory).

If your /tmp is a tmpfs filesystem, a reboot will restore everything. Otherwise, run chmod 1777 /tmp.

```
stat /tmp
  File: /tmp
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 252,0    Inode: 29360129    Links: 22
Access: (1777/drwxrwxrwt)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-11-05 08:56:13.793197868 -0700
Modify: 2024-11-05 09:08:24.284232293 -0700
Change: 2024-11-05 09:08:24.284232293 -0700
 Birth: 2024-11-03 08:50:34.693719092 -0700

```

Additionally, a lot of files in /tmp need to be private. However, at least one directory critically needs to be world-readable: /tmp/.X11-unix, and possibly some other similar directories (/tmp/.XIM-unix, etc.). The following command should mostly set things right:

EDIT:
```
 apt policy fuse3
fuse3:
  Installed: 3.14.0-9
  Candidate: 3.14.0-9
  Version table:
 *** 3.14.0-9 500
        500 http://archive.ubuntu.com/ubuntu plucky/main amd64 Packages
        100 /var/lib/dpkg/status


```

---

### Post by com-c on 2024-11-05
> **1fallen2 said:**
> Some Appimages need "elevation" to run (sudo) but it would ideal if it prompted for the root password first.

What appimage is it?



It seems that the problem is for all appimages, I did the test with balenaEtcher-1.7.9-ia32.AppImage, balenaEtcher-1.18.11-x64.AppImage, LM_Studio-0.3.5.AppImage,


What I don't understand and what drives me crazy is that it works perfectly under gnome but not under xfce (same PC with multi desktop). In Settings>>Sessions and Startup>>Advanced Tab>>Check Launch Gnome services on startup , Gnome services at startup is already checked


> 

The normal settings for /tmp are 1777 aka "a=rwx,o+t", which ls shows as drwxrwxrwt.(see my code box) That is: wide open, except that only the owner of a file (or of /tmp, but in that case that's root which has every right anyway) can remove or rename it (that's what this extra t bit means for a directory).

If your /tmp is a tmpfs filesystem, a reboot will restore everything. Otherwise, run chmod 1777 /tmp.

```
stat /tmp
  File: /tmp
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 252,0    Inode: 29360129    Links: 22
Access: (1777/drwxrwxrwt)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-11-05 08:56:13.793197868 -0700
Modify: 2024-11-05 09:08:24.284232293 -0700
Change: 2024-11-05 09:08:24.284232293 -0700
 Birth: 2024-11-03 08:50:34.693719092 -0700

```

Additionally, a lot of files in /tmp need to be private. However, at least one directory critically needs to be world-readable: /tmp/.X11-unix, and possibly some other similar directories (/tmp/.XIM-unix, etc.). The following command should mostly set things right:

EDIT:
```
 apt policy fuse3

fuse3:
  Installed: 3.14.0-9
  Candidate: 3.14.0-9
  Version table:
 *** 3.14.0-9 500
        500 http://archive.ubuntu.com/ubuntu plucky/main amd64 Packages
        100 /var/lib/dpkg/status


```



```
captain@captain-PC-master:~$ stat /tmp  
Fichier : /tmp
   Taille : 4096          Blocs : 8          Blocs d'E/S : 4096   répertoire
Périphérique : 259/5    In&#339;ud : 11796481    Liens : 18
Accès : (1777/drwxrwxrwt)  UID : (    0/    root)   GID : (    0/    root)
Accès : 2024-11-04 16:29:40.763990112 +0100
Modif. : 2024-11-05 14:30:38.638112804 +0100
Changt : 2024-11-05 14:30:38.638112804 +0100
  Créé : 2024-11-02 20:48:55.301638862 +0100



```

```
captain@captain-PC-master:~$ apt policy fuse3
fuse3:
  Installé : 3.14.0-5build1
  Candidat : 3.14.0-5build1
 Table de version :
 *** 3.14.0-5build1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status



```

This did not change the problem

---

### Post by 1fallen on 2024-11-05
I can only speak on XFCE, I have no interest in Gnome. (Sorry)
Etcher as you know needs elevated privileges:
```
&#9472;> '/home/me/balenaEtcher-1.9.0-x64.AppImage' 
[52757:1105/114118.181215:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /tmp/.mount_balenasyf1NY/chrome-sandbox is owned by root and has mode 4755.
/tmp/.mount_balenasyf1NY/balena-etcher: line 10: 52757 Trace/breakpoint trap   (core dumped) "${script_dir}"/balena-etcher.bin "$@"
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
But when ran as root:
```
sudo '/home/me/balenaEtcher-1.9.0-x64.AppImage' 
```
It works...and I trust this appimage so this will also work, but not recommended:
```
'/home/me/balenaEtcher-1.9.0-x64.AppImage' --no-sandbox
```

All my non Buntu XFCE installs do not need this wonky work around.

Just Xubuntu...

---

### Post by com-c on 2024-11-05
> **1fallen said:**
> I can only speak on XFCE, I have no interest in Gnome. (Sorry)


I also use xfce since xubuntu 20, I had no problem on xubuntu 20 or xubuntu 22, the problem occurred after the update to xubuntu 24. I thought the problem came from the update and that's why I reinstalled everything. Unfortunately for me the problem persists.


> 
Etcher as you know needs elevated privileges:
```
&#9472;> '/home/me/balenaEtcher-1.9.0-x64.AppImage' 
[52757:1105/114118.181215:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /tmp/.mount_balenasyf1NY/chrome-sandbox is owned by root and has mode 4755.
/tmp/.mount_balenasyf1NY/balena-etcher: line 10: 52757 Trace/breakpoint trap   (core dumped) "${script_dir}"/balena-etcher.bin "$@"
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
But when ran as root:
```
sudo '/home/me/balenaEtcher-1.9.0-x64.AppImage' 
```


```
captain@captain-PC-master:~$ sudo '/home/captain/Modèles/appimage/LM_Studio-0.3.5.AppImage'
 [sudo] Mot de passe de captain : 
[1106/003247.026876:FATAL:electron_main_delegate.cc(294)] Running as root without --no-sandbox is not supported. See https://crbug.com/638180.
Trap for breakpoint and trace

```
unfortunately it doesn't work for me
> 
It works...and I trust this appimage so this will also work, but not recommended:
```
'/home/me/balenaEtcher-1.9.0-x64.AppImage' --no-sandbox
```

indeed I agree with you, it is not safe to launch outside sandbox, just like The only working solution I found, but it is non-persistent and also not very secure:```
[COLOR=#333333][FONT=Verdana]sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
sudo sysctl -w kernel.apparmor_restrict_unprivileged_unconfined=0[/FONT][/COLOR]

```> 
All my non Buntu XFCE installs do not need this wonky work around.

Just Xubuntu...

---

### Post by Tadaen_Sylvermane on 2024-11-05
I just gave up the appimages personally. I liked and used them when I could but once they started causing problems that required the --no-sandbox option then the benefit was gone. Distrobox and installing inside an isolated container of whichever distro is ideal for the package is a much superior solution with the exact same end result of using the home dir natively for me personally. I think it will be awhile before that gets dethroned. It's just perfect from my view. Obviously a bit more involved, price one pays for relative security + convenience.

---

### Post by com-c on 2024-11-05
> **Tadaen_Sylvermane said:**
> I just gave up the appimages personally. I liked and used them when I could but once they started causing problems that required the --no-sandbox option then the benefit was gone. Distrobox and installing inside an isolated container of whichever distro is ideal for the package is a much superior solution with the exact same end result of using the home dir natively for me personally. I think it will be awhile before that gets dethroned. It's just perfect from my view. Obviously a bit more involved, price one pays for relative security + convenience.

Hello, I don't really like appimages, snaps, flatpaks, ... not by conviction, but rather by habit of .deb (and .rpm for other distributions). I didn't know Distrobox, and in view of the few searches I just did on the subject, this could indeed be a very good solution to my problem and open me to possibilities on other subjects. thank you

---

