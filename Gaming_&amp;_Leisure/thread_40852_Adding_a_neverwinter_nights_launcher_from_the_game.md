---
title: "Adding a neverwinter nights launcher from the games menu."
date: 2005-06-10
forum: Gaming &amp; Leisure
---

### Post by RaymondQE on 2005-06-10
This is a miniguide to adding a neverwinter menu item in the games menu.

First make sure you've followed all of the previous instructions for installing the program.

Next run:

```
sudo gedit /usr/share/applications/nwn.desktop
```

add the following text into the file replacing the /path/to/neverwinter with your neverwinter nights directory.

```

[Desktop Entry]
Name=Neverwinter Nights
Comment=Neverwinter Nights
Exec=sh /path/to/neverwinter/nwn
Icon=/path/to/neverwinter/nwn.xpm
Terminal=false
Type=Application
Categories=Application;Game;
```

Create a backup of the nwn script in the game directory

```
cd /path/to/neverwinter
cp nwn nwn.backup
```

Edit the nwn file

```
gedit nwn
```

add the line to the file below the '# This script runs Neverwinter Nights from the current directory'

```
cd /path/to/neverwinter/
```

If all goes well, you will be able to run the program from the APP->games menu.

---

