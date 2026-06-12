---
title: "don't know how to install lastfm radio player?"
date: 2005-12-17
forum: Desktop Environments
---

### Post by colly3 on 2005-12-17
hello,

i've been trying to install LastfmLinux-1.0.5.tar.bz2 radio player.
I don't know which command to use to install this package. 
If you can give me a hint howto, i would be pleased.

---

### Post by amohanty on 2005-12-17
1. Fire up terminal:
Applications->Accesories->Terminal

2. Copy the file to your home directory
Places->Home and just drag and drop.

3. Unzip file, in the terminal:
> tar xjf LastfmLinux-1.0.5.tar.bz2
This will unzip the binary in your home account. Its Qt based so if you are using Gnome, the fonts might be a bit ugly. 

4. Run it:
./<filename of unzipped file>


HTH
AM

---

### Post by Ampersand on 2005-12-17
you just need to extract the tar.bz2 file (if you right click on it, it should have an option to open it with 'archive manager'). Alternatively, you can use a terminal with the command
```
tar -xvf LastfmLinux-1.0.5.tar.bz2
```
Then to run it, either double click on the Player file in the Last.fm-1.0.5 folder, or if you're in the terminal, type
```

cd Last.fm-1.0.5
./player

```

---

### Post by colly3 on 2005-12-17
thanks.

---

