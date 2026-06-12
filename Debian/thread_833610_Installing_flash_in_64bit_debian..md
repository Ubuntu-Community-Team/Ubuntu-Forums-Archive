---
title: "Installing flash in 64bit debian."
date: 2008-06-18
forum: Debian
---

### Post by whitefang5412 on 2008-06-18
I installed a 64 bit version of debian lenny testing. How the heck do I install flash on here? Is there any support? It always worked right in ubuntu...Help ASAP before I go with the i386 version.

---

### Post by FoundmyTux on 2008-06-19
Go to [http://www.debian-multimedia.org/]("http://www.debian-multimedia.org/") and follow instructions to install packages into your /etc/apt/sources.list.

From a terminal type su and enter your root password.

Type aptitude install flashplayer-mozilla

---

### Post by benuski on 2008-06-21
Or just enable the official debian "contrib" repository.  Add "contrib" (without the quotes) after where ever it says "main" in your /etc/apt/sources.list file.  

Then you can just "aptitude install flashplugin-nonfree", or install the flashplugin-nonfree package using your favorite graphical interface to apt.

---

### Post by Shakey_Jake33 on 2008-06-24
That no longer works, as far as I know.

Follow this guide [http://wiki.soslug.org/wiki/how_to_install_flash_player_in_debian_etch_64_bit_with_iceweasel](http://wiki.soslug.org/wiki/how_to_install_flash_player_in_debian_etch_64_bit_with_iceweasel)

I know it's for Etch, but it's the same procedure.

---

### Post by benuski on 2008-06-25
The official flashplugin-nonfree package is available in Debian unstable, and the Debian Multimedia version is available for all versions of Debian.  Both of fully supported by Debian Developers, and are as simple as an aptitude install.

---

