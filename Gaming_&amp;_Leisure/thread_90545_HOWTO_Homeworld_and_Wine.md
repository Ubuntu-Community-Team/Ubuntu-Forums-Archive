---
title: "HOWTO: Homeworld and Wine"
date: 2005-11-15
forum: Gaming &amp; Leisure
---

### Post by tonderai on 2005-11-15
I had this strange error with Homeworld and wine (ver. 0.9.1) where the game would install fine from the cdrom, but would refuse to detect it when run - giving a 'invalid or missing homeworld CD error'. I finally managed to correct it :D

1.) Run winecfg and click 'autodetect' on the 'drives' tab, making sure your cdrom drive is listed.

2.) Run regedit and go to HKEY_LOCAL_MACHINE/Software/Wine/Drives. Set the 'data' field for D: (or whatever drive letter your CD drive is set to in winecfg) to 'cdrom' instead of 'hd'.

Homeworld now recognises the cd and runs!

**************************************************
Another problem is that homeworld will not run from anywhere but the directory in which it is installed - giving the error 'Can't open file: Homeworld.big'.

To solve this you can create a shell script to change directory and run homeworld from there.

1.) ```
sudo gedit /usr/bin/homeworld.sh
```

2.) Paste the following lines into the new file:
```

cd /home/username/.wine/drive_c/Sierra/Homeworld/
wine homeworld.exe

```
(substituting your username to reflect the homeworld install directory)

3.) Make the script executable
```
sudo chmod +x /usr/bin/homeworld.sh
```

Now you can execute 'homeworld.sh' from anywhere, or even make a shortcut from your gnome/kde panel.

**************************************************
Hope this is of help - it is certainly worth it for such a classic game!

---

### Post by slux on 2005-11-15
There's also a native port for Homeworld: [http://www.thereisnospork.com/projects/homeworld/](http://www.thereisnospork.com/projects/homeworld/)

Not perfect but might still be nicer than WINE.

---

### Post by YokoZar on 2005-11-17
Why don't you visit the Wine application's database ( [http://appdb.winehq.org/](http://appdb.winehq.org/) ) and become the supermaintainer for Homeworld?  You certainly know what you're doing :)

---

### Post by tonderai on 2005-11-17
[QUOTE=YokoZar]Why don't you visit the Wine application's database ( [http://appdb.winehq.org/](http://appdb.winehq.org/) ) and become the supermaintainer for Homeworld?  You certainly know what you're doing :)[/QUOTE]

I wouldn't go that far! The first I stumbled across, and the second was inspired by the Limewire shell script. But, thanks for the compliment :D

---

### Post by mega.deb on 2007-06-23
thank you !!

---

