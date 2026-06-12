---
title: "Problem with Gnome Shell theme on 11.10"
date: 2011-10-15
forum: Desktop Environments
---

### Post by aafgarci on 2011-10-15
Hi,

I am having a problem with Gnome Shell after upgrading to Ubuntu 11.10. The desktop theme looks weird and I am not able to change it.

On 11.04, the solution was to remove gnome-accessibilty-themes and installing gnome-default-themes, but this is not working with new Gnome, since they have mutual depence: if I remove one, both will go away; if installing one, both will be present.

Any ideas? Thanks.

---

### Post by collisionystm on 2011-10-15
> **aafgarci said:**
> Hi,

I am having a problem with Gnome Shell after upgrading to Ubuntu 11.10. The desktop theme looks weird and I am not able to change it.

On 11.04, the solution was to remove gnome-accessibilty-themes and installing gnome-default-themes, but this is not working with new Gnome, since they have mutual depence: if I remove one, both will go away; if installing one, both will be present.

Any ideas? Thanks.


What does it look like? 

Like this? [http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/)

If so, thats normal.

---

### Post by aafgarci on 2011-10-15
Very funny, thanks.

No, this is how it looks:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204418&stc=1&d=1318694463[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204419&stc=1&d=1318694463[/IMG]

---

### Post by Spr0k3t on 2011-10-15
You should try changing the theme using the gnome-tweak-tool.

```
sudo apt-get install gnome-tweak-tool
```

It will show up as Advanced Settings in the applications menu.

---

### Post by drawkcab on 2011-10-15
Might be an artifact of upgrading.  I had some weird problems with gnome shell until I did a clean install.  Might have to do with compiz or gnome 2 files hanging around and mucking things up.

---

### Post by aafgarci on 2011-10-15
I tried changing the theme using the tweaking, still not working:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204438&stc=1&d=1318701437[/IMG]

My installation is a fresh one (not an upgrade).

Very sad, since I like Gnome Shell a lot, and it works pretty well in Ubuntu 11.04, although without some new funcionalities.

---

### Post by drawkcab on 2011-10-15
dang.  maybe your .iso is corrupt?

---

### Post by aafgarci on 2011-10-15
The .iso is OK. Something weird is going on...

---

### Post by sam45 on 2011-10-15
Are you using an ATI graphic card?
If so, this thread may help you

[http://ubuntuforums.org/showthread.php?t=1859626&page=2](http://ubuntuforums.org/showthread.php?t=1859626&page=2)

---

### Post by Bartcore3 on 2011-10-15
I'm having simular problems.
I don't think it's because of upgrading. I removed the previous version and did a clean install (Wubi).
Unity works fine but Gnome doesn't :(

EDIT: My laptop uses an ATI graphic card

---

### Post by Bartcore3 on 2011-10-15
Thanks! Worked for me :)

---

### Post by aafgarci on 2011-10-15
I am also using ATI, so the solution worked for me as well! Thanks a lot.

Just to help others, I'm including the commands here:

1. sudo /usr/share/ati/fglrx-uninstall.sh # (if it exists) edit: mine did not
2. sudo apt-get remove --purge fglrx
3. sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg- video-radeon 
4. sudo apt-get install xserver-xorg-video-ati
5. sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
6. sudo dpkg-reconfigure xserver-xorg

reboot, and voilá!
:D

---

