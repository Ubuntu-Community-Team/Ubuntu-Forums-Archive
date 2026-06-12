---
title: "Ubuntu keeps giving me an error whenever i run Sinaptic"
date: 2005-12-10
forum: Desktop Environments
---

### Post by Zyren on 2005-12-10
I recently reformatted and installed linux, so i ran easy breezy to get all the applications i needed back. After i ran it, i tried to open MPlayer so i could want a MWV file. It kept giving me an error with some font, so i tried to reinstall it. However, whenever i load synaptic or try to reinstall MPlayer using the terminal, i get this error:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

anyone know why i get that?

thanks

---

### Post by linbetwin on 2005-12-10
[quote=Zyren]I recently reformatted and installed linux, so i ran easy breezy to get all the applications i needed back. After i ran it, i tried to open MPlayer so i could want a MWV file. It kept giving me an error with some font, so i tried to reinstall it. However, whenever i load synaptic or try to reinstall MPlayer using the terminal, i get this error:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

anyone know why i get that?

thanks[/quote]

It asks for your Ubuntu CD. You can disable that in your repositories list. In Synaptic: Settings -> Repositories and deselect Ubuntu CD.

---

### Post by PatrickMay16 on 2005-12-10
I had this problem a while ago. Here was the solution:

Open the terminal. Then, type this command:
```

sudo gedit /etc/apt/sources.list

```

You'll see something like this 
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

```
somewhere in the sources.list file. Delete it, and save the changes. Now, run this command:
```

sudo apt-get update

```
After that, find your ubuntu install CD, and insert it into your CD drive. Open synaptic, then go to Edit -> Add CD-ROM...

Hope this helps.

---

### Post by Zyren on 2005-12-10
Thanks PatrickMay16, that worked. However, im still gettting an error in MPlayer, even after i reinstall it.

New_face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.tff)

Im fairly new to linux (only started it last week), but isnt ~ home? so why is it trying to look for a directory in home? I looked in /usr/share/mplayer/skins and i dont see a subfont file. How come when i update the program it doesnt give me the file? I dont really know how to fix it, or find the file its looking for.

---

### Post by arnieboy on 2005-12-10
[QUOTE=Zyren]Thanks PatrickMay16, that worked. However, im still gettting an error in MPlayer, even after i reinstall it.

New_face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.tff)

Im fairly new to linux (only started it last week), but isnt ~ home? so why is it trying to look for a directory in home? I looked in /usr/share/mplayer/skins and i dont see a subfont file. How come when i update the program it doesnt give me the file? I dont really know how to fix it, or find the file its looking for.[/QUOTE]
try doing:
```
sudo apt-get install mplayer-fonts
```

---

### Post by Zyren on 2005-12-10
Thanks arnieboy, that worked.

---

