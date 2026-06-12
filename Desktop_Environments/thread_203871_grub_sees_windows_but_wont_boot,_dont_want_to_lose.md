---
title: "grub sees windows but wont boot, dont want to lose ubuntu desktop by reinstalling"
date: 2006-06-26
forum: Desktop Environments
---

### Post by aceron on 2006-06-26
bit of a problem. I had ubuntu entirely on my laptop, then i just use my windows recovery cds to wipe it out (i had dapper running on my desktop). But windws would never boot, grub was still in the mbr. So i installed dapper via live cd on a seperate partition keeping windows on the hd. at first grub did not even see the xp drive, i fixed that but now when i try to load it from grub it flashes:
savedefault
makeactive
chainloader +1
then comes back to grub boot sreen (i can get into dapper just fine from this though)
my grub menu looks normal

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1


so i'm really interested in a solution to this if anyone has had the same prob

also if in uninstalled grub from the mbr, would i then boot from windows?
if so then i could reinstall grub from there an it sould find xp since its reinstalling grub eh?
if i cant just fix grub (which is what I want to do) then i'll just make a win floppy an fxmbr and re install dapper, thanks

---

### Post by nquinnathome1 on 2006-06-26
I know there's a Windows Recovery command you can use via the WinXP CD; I think it's fixmbr however this completely removes Grub from the startup equation and replaces it with the default Windows bootloader; i'm not sure once you've done that if you can then install Grub by itself to get back to Ubuntu again; maybe someone else knows.

---

### Post by aceron on 2006-06-26
[QUOTE=nquinnathome1]I know there's a Windows Recovery command you can use via the WinXP CD; I think it's fixmbr however this completely removes Grub from the startup equation and replaces it with the default Windows bootloader; i'm not sure once you've done that if you can then install Grub by itself to get back to Ubuntu again; maybe someone else knows.[/QUOTE]

yes i could, and yes thats the command, but i cant get into DOS on the rcovery cd i have i think you can only do that with win install cds

---

### Post by ajgreeny on 2006-06-26
I believe you can do the fixmbr using a windows98 floppy if needed.  Have a look at the following:-

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

which should help a great deal with your problem, but assumes you have a floppy for the win98 disk startup.  If you do have a floppy you can also put grub on a floppy before you reinstall mbr, by typing in a terminal:-
*sudo grub-install /dev/fd0*

If you get an error message about not in bios or something similar, edit your /boot/grub/device.map file by adding the line:-
*(fd0)  /dev/fd0*
to the bottom and all should go OK if you try grub-install again.  Then when you want to run ubuntu after the mbr is restored all you need to do is boot with the floppy in drive, and bingo, you should get the grub menu.

---

