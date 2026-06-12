---
title: "wp_tray is not working"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Marcos.Rufino on 2006-06-14
I've installed wp_tray through Synaptic but nothing happens. It doesn't have any icon nor has an option to include the applet in the Gnome toolbar. Does anyone know how could one solve this?

I've already read the Wiki page about how to install the wp_tray tarball **but that is not what I want**. I suppose that once a package is in the repositories it should be installed like a breezy... wishiful thinking

Anyway, Dapper Drake is pissing me off with the flaws with apt-get or Synaptic. Many applications I installed don't appeared with its original icon; and I'm talking about popular applications like ipodder, celestia, stellarium. Many others don't even appear in Gnome menu.

---

### Post by Marcos.Rufino on 2006-06-20
Now, wp_tray appears in Gnome menu and in the notification area when opened, but it doesn't work! When I try to add some images, the "add" button doesn't work; it's like a sugar pill, it's there, but do nothing.

---

### Post by anil_robo on 2006-07-03
Similar problem here. Confirmed.

I have just installed wp_tray via synaptic, and it shows an icon in the tray (thumbnail of my current wallpaper). However, it doesn't do what it's supposed to do - it neither searches for wallpapers, nor changes them. The dialog boxes in the configuration are not "clickable" and seem as if the programmer forgot to assign actions to the buttons :)

---

### Post by autocrosser on 2006-07-09
The "way" to make wp_tray work--

Make sure that you have gconf (will show as Configuration Editor)--/System Tools/Configuration Editor/apps/wp_tray

Check-mark all the boxes & where it has dir_list---put in the path to you wallpaper (mine is /home/dean/backgrounds/desktop (MUST NOT HAVE SPACES IN PATH)

change your n_timeout to what you want change period to be.

Any other questions---just ask!!!

---

### Post by anil_robo on 2006-07-09
You're the man! Finally I could get this working after six months or so! Bravo! :D

---

### Post by autocrosser on 2006-07-09
Thank you--I've been trying to build the most current version of wp_tray & so far hit a dead end--can't get all the depends sorted out--It sort of sounds like the maintainer may have dropped the app-the last update was from 2005 Dec.

More Info: I've downloaded both .50 & .51 in .tar & .51 in .rpm--the .tar(s) won't work without libboostfilesystem.so (and I can't seem to get enough from boost libs in Dapper) & the .rpm installs but throws a error (installs as a panel applet)--So, I'm at a deadend as to installing a newer version :(

---

### Post by Marcos.Rufino on 2006-07-10
Thank you autocrosser. Now, everything is working fine.

---

### Post by autocrosser on 2006-07-10
Very Good--Glad I could help..

---

