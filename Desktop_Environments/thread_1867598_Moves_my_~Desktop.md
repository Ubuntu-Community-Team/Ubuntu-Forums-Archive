---
title: "Moves my ~/Desktop"
date: 2011-10-23
forum: Desktop Environments
---

### Post by r_anjit on 2011-10-23
[SIZE=2]I accidently moved my desktop to another location wit sudo powers .

[/SIZE][INDENT][SIZE=2][COLOR=Red]$ sudo mv ~/Desktop /var/cache/apt/archives[/COLOR][/SIZE]
[/INDENT][SIZE=2]I realising the  mistake brought it back 

[/SIZE][SIZE=2][COLOR=Red]         $sudo mv /var/cache/apt/archives ~[/COLOR][/SIZE]

[SIZE=2]But now it does not work and my desktop shows the home folder contents along with the Desktop folder as a folder . 

How can I bring back the desktop..association...I have messed up with the settings it seems .

Thanks !![/SIZE]

---

### Post by oldos2er on 2011-10-23
Run ```
gksudo nautilus
``` and look for your Desktop files in /root. ```
mkdir Desktop
``` should give you back a Desktop folder; run it without sudo privileges from within your home folder.

"sudo mv /var/cache/apt/archives ~" would place files in root's home folder, not your user's home.

---

### Post by matt_symes on 2011-10-23
Hi

If oldos2ers advice does not completely fix it you may need to edit your ~/.config/user-dirs.dirs file.

Make it look like this.
```

matthew@matthew-Aspire-7540:~$ cat ~/.config/user-dirs.dirs 
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
matthew@matthew-Aspire-7540:~$ 
```

Kind regards

---

### Post by r_anjit on 2011-11-09
" Thanks both of you above ..... I changed the concerned lines in ~/.config/user-dirs.dirs and my desktop is working fine again ....Thanks again !!! "

---

