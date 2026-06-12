---
title: "Unpacking .sav files"
date: 2009-07-13
forum: Gaming &amp; Leisure
---

### Post by Locke Cole on 2009-07-13
[FONT=Trebuchet MS][SIZE=3][COLOR=DarkRed]Well... First, sorry for my english. I have a problem with Mednafen. Look the sav files (usually in /home/.mednafen/sav):

[IMG]http://img73.imageshack.us/img73/9260/capturadetelasavesnaveg.png[/IMG]

When I try to extract the files, the system shows an error message. I tried it with Ark too, but it doesn't work...

How can I unpack it?
[/COLOR][/SIZE][/FONT]

---

### Post by DoktorSeven on 2009-07-13
Mednafen .sav files aren't archives, they're binary dumps of game saves, used only by mednafen.  

So there's nothing to extract.

---

### Post by Jimleko211 on 2009-07-13
They aren't just used by mednafen, but by all GBA emulators (and indeed, the GBA itself if you get a flash cart or something).  But yeah, that's not an archive.

---

### Post by Locke Cole on 2009-07-13
I sent this question because both Mednafen and VBA-M use .sav files. I would like to play my games in VBA-M, using the old saves created by Mednafen.

The problem: apparently, .sav files of Mednafen and VBA-M isn't compatible.

A regular .sav file in VBA-M is like:

Name - Mario Kart - Super Circuit.sav
Type: unknown (application/octet-stream)
Icon: It's like texts icons made by Gedit

A regular .sav file in Mednafen is like:

Name - Mario Kart - Super Circuit.784a036ff1aae709e90167186639b75e.sav
Type: Gzip Package (application/x-gzip)
Icon: The icon is a package

So, my wish is to play games in VBA-M using the old save slots, created by Mednafen (both .sav).

Is it possible?

---

### Post by Locke Cole on 2009-07-14
Bump.

---

### Post by DoktorSeven on 2009-07-14
Doubtful, different emulators save things in different ways.  You could search any mednafen and/or vba-m documentation to see if there is any sort of way to convert back and forth but the two aren't immediately usable in the other.

---

### Post by BoyOfDestiny on 2009-07-14
One, mednafen does compress its save data to gunzip format, unless you specify otherwise.

Look inside ~/.mednafen/mednafen.cfg
```
;Disable gzip compression when saving save states and backup memory.
filesys.disablesavegz 0

```

Change that to a 1, and mednafen will no longer compress your .sav.

Mine do open fine however in "Archive Manager", so it's strange that yours does not.

As for using the .sav in different emulators, **the answer is yes**. With the right hardware, you could even use it in a cartridge. It is simply the save ram, battery backed up memory. Things like save states are different between emulators, save ram isn't :P

P.S. There is also a newer mednafen than the one you have if on ubuntu interpid.
[http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)
Also, Locke Cole, your English is excellent.

---

### Post by Bölvaður on 2009-07-14
try installing gzip
it is a shot in the dark, but hey... if the guy above me is correct this might be it.

---

### Post by Locke Cole on 2009-07-14
[FONT=Trebuchet MS][SIZE=3][COLOR=DarkRed]Thanks, [BoyOfDestiny]("http://ubuntuforums.org/member.php?u=859"), your hint worked perfectly!

Now I can transfer saves from Mednafen to VBA-M easily.

So, there is a new version of Mednafen? Thanks to remember it too.
[/COLOR][/SIZE][/FONT]

---

