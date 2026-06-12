---
title: "A wtf moment that needs to be solved"
date: 2007-01-02
forum: Gaming &amp; Leisure
---

### Post by rekahsoft on 2007-01-02
I am installing Halflife 2, Half life 1 source, counterstrike source and have ran into a really dumb problem. I am using wine version 0.9.28 and installing the games from the Half life 2 Game of the Year Edition. I first installed the tahoma font then installed steam with no problems. After that i started the install of Half life 2 by doing the following:```
wine msiexec /i /media/cdrom0/hl2.msi
```The install has gone fine so far but now i am having a problem...It is asking for the second disk but my cannot remove it using the button on my disk drive and i can't unmount it because it is "in use". What do i do?

---

### Post by d3v1ant_0n3 on 2007-01-02
Does steam work the same way on Linux as it does with windows? i.e. you could enter the cd key for HL2, and just download the files. Might take a while tho. Although it *will* save you the hassle of having to update HL2.

---

### Post by rekahsoft on 2007-01-02
> **d3v1ant_0n3 said:**
> Does steam work the same way on Linux as it does with windows? i.e. you could enter the cd key for HL2, and just download the files. Might take a while tho. Although it *will* save you the hassle of having to update HL2.

hmmm...i guess i will have to do that :'(:'(:'(

---

### Post by albeano2004 on 2007-01-02
Why not just copy each disc to a temporary directory on your hdd, then delete once install has finished (assuming you have enough space)? That's what I have done in the past for other multiple disc games.

---

### Post by rekahsoft on 2007-01-02
> **albeano2004 said:**
> Why not just copy each disc to a temporary directory on your hdd, then delete once install has finished (assuming you have enough space)? That's what I have done in the past for other multiple disc games.

I cannot do that because it does not allow me to specify a directory.

---

### Post by wounded on 2007-01-03
Well, I think what was meant by the directory thing was make an ISO file of each disc before hand (It can be done with a single command although I can't recall the exact syntax) and then "sudo mount /path/to/iso1 /media/cdrom0"

Then when it wants disc to

sudo umount /media/cdrom0
sudo mount /path/to/iso2 /media/cdrom0

And the installer will treat it as if it was an actual cd.

As for the disc drive not opening make sure you dont have the folder you are trying to unmount open in nautilus/thunar/konqueror/whatever or the active directory of a terminal thats open or something silly like that. Anything like that will make it not unmount.

---

### Post by rekahsoft on 2007-01-03
> **wounded said:**
> Well, I think what was meant by the directory thing was make an ISO file of each disc before hand (It can be done with a single command although I can't recall the exact syntax) and then "sudo mount /path/to/iso1 /media/cdrom0"

Then when it wants disc to

sudo umount /media/cdrom0
sudo mount /path/to/iso2 /media/cdrom0

And the installer will treat it as if it was an actual cd.

As for the disc drive not opening make sure you dont have the folder you are trying to unmount open in nautilus/thunar/konqueror/whatever or the active directory of a terminal thats open or something silly like that. Anything like that will make it not unmount.

smart :) thanks...i have given up and have decided i will not support games that do not support linux. At least for now...i am not much of a gamer anyways

---

### Post by diepruis on 2007-01-03
When something doesn't want to unmount, you can also try
```

sudo umount /path/to/device_or_directory -l

```
The -l switch will unmount it regardless of whether it's in use. Don't use this on writeable media though.

---

### Post by Enverex on 2007-01-10
You can also try going back to the terminal you ran Wine from, hitting "ctrl+z" then chdir'ing from the CD to another folder like / then typing "fg" then seeing if it will let you eject.

---

### Post by shawnrgr on 2007-05-12
why not just "wine eject"

---

