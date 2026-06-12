---
title: "Quake 3 on Dapper 64"
date: 2006-05-30
forum: Gaming &amp; Leisure
---

### Post by R3linquish3r on 2006-05-30
Well I made the switch to Dapper 64 bit (from 32) and I'm having some trouble setting up Quake 3 Arena. I go to install the 2.31b patch and I get the following error:

```
ed@ubuntu:/media/sda1/Games/Quake 3$ sudo ./linuxq3apoint-1.32b.x86.run 
Verifying archive integrity... All good.
Uncompressing Quake III Arena Point Release 1.32b ...................................................................................................................................................
This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com
The setup program seems to have failed on x86_64/glibc-2.0

Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com
The program returned an error code (1)
```

Obviously the installer is made for 32 bit and I've looked all around for a 64 version of it but havent been able to find one. Does anyone know of a way to install the patch on 64 or where I can find one? I would like to avoid chroot if at all possible.

---

### Post by R3linquish3r on 2006-05-30
Can anyone help?

---

### Post by R3linquish3r on 2006-05-31
Well I managed in my searching to find the source code for the installer. Could anyone explain to me how I use this to make the isntaller? It would be appreciated :)

---

### Post by jdodson on 2006-05-31
[QUOTE=R3linquish3r]Well I managed in my searching to find the source code for the installer. Could anyone explain to me how I use this to make the isntaller? It would be appreciated :)[/QUOTE]

[http://www.icculus.org/quake3/](http://www.icculus.org/quake3/)

the directions on the site should help you get it working.

---

### Post by R3linquish3r on 2006-06-01
I already checked them out actually. Punkbuster isn't suported in those pacakges so they're no good for me.

---

### Post by R3linquish3r on 2006-06-02
Well I found a glitch with what I thought earlier. I just tried running the isntall in a chroot and I got the following error which is the same as before.

```
ed@ubuntu:/media/sda1/Games/Quake 3$ sudo ./linuxq3apoint-1.32b.x86.run 
Verifying archive integrity... All good.
Uncompressing Quake III Arena Point Release 1.32b ...................................................................................................................................................
This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com
The setup program seems to have failed on x86_64/glibc-2.0

Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com
The program returned an error code (1)
```

If anyone would like to look at the available source code and maybe you could find out how to compile it (still fairly new to that ](*,)  ) here is a link to the download:

[http://www.fileshack.com/file.x?fid=7547](http://www.fileshack.com/file.x?fid=7547)

---

### Post by R3linquish3r on 2006-06-02
To Teroedni:

Results from ed@ubuntu:~/quake3-1.32b/code/unix$ sudo sh cons -- gcc=gcc-4.0 g++=g++-4.0

: No such file or directory
ed@ubuntu:~/quake3-1.32b/code/unix$ sudo sh cons -- gcc=gcc-4.0 g++=g++-4.0
: command not found
: command not found
cons: line 16: syntax error near unexpected token `('
'ons: line 16: `use vars qw( $CVS_id $CVS_ver $ver_num $ver_rev $version );

Results from ed@ubuntu:~/quake3-1.32b/code$ ./unix/cons -- gcc=gcc-4.0 g++=g++-4.0

: No such file or directory


Result from ed@ubuntu:~/quake3-1.32b/code$ sudo sh /unix/cons -- gcc=gcc-4.0 g++=g++-4.0

sh: /unix/cons: No such file or directory

AN\ny more clues man?

---

### Post by R3linquish3r on 2006-06-03
Does anyone have any ideas on how I can get this running? Now that I've gotten this far with 64x I don't want to give it up for a game, but I don't want to give this game up either :p . It's just a stupid .run file that is the wrong architecture and ID doesn't have a 64x version. Is there anyway to force the architecture like with a .deb or anyhing else I can do?

---

### Post by JoWilly on 2006-06-03
It's looking for a 32 bit glibc. Are you sure your ia32 libs are installed (dont' know if the need lib is included)?

Is so, have you tried to copy a 32bit glibc over ?

But if this installer also checks for the architecture (it maybe the case) your're screwed with this and as you did, rebuilding the installer or extracting the files and copying them over manually (installing the files manually) are your only options.

---

