---
title: "UT2004 won't start after upgrade"
date: 2004-12-29
forum: Gaming &amp; Leisure
---

### Post by Dylanby on 2004-12-29
Last night I upgraded my UT2004 ECE to 3339 so that I could install some mods (bought the game last Friday). The game was working great (single player) prior to this.

I'm running Ubuntu AMD64.

Now when I try to start the game or one of the mods I get:
```
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory
```

Last night when I installed everything it was done consecutively. The upgrade followed by four mod installations, one after the other. So I'm not sure what broke what.

I initially installed UT2004 into my home directory so that's where I installed the mods too.

My 'libSDL-1.2.so.0' in in '/home/dylan/ut2004/system'. 

This is probably an easy thing to fix but I'm lost. I'd like to know how to fix it, but also I'd like to know why it broke too.

---

### Post by ubuntu.daemon on 2004-12-29
How did you get your ut2004 to work? I get a flash screen(the epic one) and the the screen goes black like it loads then it reverts back to what i was doing beforehand.
This is from my other post:
redxiii@xavier:~ $ ut2004
Xlib: extension "XFree86-DRI" missing on display ":0.0".
WARNING: ALC_EXT_capture is subject to change!
Xlib: extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History:

Exiting due to error

that is what i get!!!  Let me know how you got urs to work!! Though now i am gonna try the loki installer you recommended then i will see.

---

### Post by Dylanby on 2004-12-29
Did you install the drivers for video card?
I used this howto:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

---

### Post by Kareema on 2004-12-30
> Last night I upgraded my UT2004 ECE to 3339 so that I could install some mods (bought the game last Friday). The game was working great (single player) prior to this.

I'm running Ubuntu AMD64.

Yep, same thing I encountered. Here's the solution:

After the update there are to kinds of executables in /usr/local/games/ut2004/System: The former 64-bit binaries have been replaced by 32-bit binaries and the 64-bit binaries have the ending "-linux-amd64".

You have two choices: Rename the 32-bit binaries (f.ex. add the ending "-linux-x86" and the 64-bit binaries (by deleting the "-linux-amd64" ending) or edit the script /usr/local/games/ut2004/ut2004 and change the line 
```
exec "./ut2004-bin" $*
```
to
```
exec "./ut2004-bin-linux-amd64" $*
```

---

### Post by Gnobody on 2005-01-31
I am having the exact same problem as mention above, however renaming the binarys didn't work for me. :(  :confused:

I am using Hoary AMD64 btw

---

### Post by jdodson on 2005-01-31
from the icculus.org site:

The Linux version needs 3339 installed AFTER the Editors' Choice Bonus Pack, since it fixes issues in the BP. If you install the Bonus Pack after 3339, you'll break your installation...in such a case, just reinstall 3339 over top of it. You must apply 3339 after the Bonus Pack. The Editors' Choice Edition disc (on sale now!) installs the Bonus Pack by default, so you can just drop 3339 on top of that without fussing.

---

### Post by Gnobody on 2005-01-31
I do not have the editors choice bonus pack and didn't install it.  :shock:

---

### Post by jdodson on 2005-01-31
[QUOTE=Gnobody]I do not have the editors choice bonus pack and didn't install it.  :shock:[/QUOTE]

you got the latest amd64 ut2004 patch?

---

### Post by Gnobody on 2005-01-31
3339?  Yes.

---

### Post by crane on 2005-01-31
OK I am running warty and did have the same error as this.

Xlib: extension "XFree86-DRI" missing on display ":0.0".
WARNING: ALC_EXT_capture is subject to change!
Xlib: extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

After some searching on unreals forums it turned out that this is a problem with the refresh rate of the monitor.
Something about not being able to find all the resolutions it needed or something, I don;t remember.

Again I an running warty but would suggest maybe tweaking your monitor refresh rates in xorg.

 Hope this helps a little.

---

### Post by dhonn on 2005-02-02
[QUOTE=Dylanby]
My 'libSDL-1.2.so.0' in in '/home/dylan/ut2004/system'. 
[/QUOTE]

try in terminal as root:

**ln -s /home/dylan/ut2004/system/libSDL-1.2.so.0 /usr/lib/libSDL-1.2.so.0**

---

### Post by winterone on 2005-02-23
Well soft link is the solution but not as above. It is far easier to rename the libSDL-1.2.so.0 to ...old in the ut2004/system and link from the file already in /usr/lib to ut2004. I did by opening a su file browser and dragging it into ut2004/system and choosing link. It was confusing because all the files are there. but when you look a your links the so.0 file in ut2004 doesn't link to the system SDL lib file! which it must to work. Hope this helped.

---

### Post by Moobert on 2005-03-19
[QUOTE=ubuntu.daemon]
redxiii@xavier:~ $ ut2004
Xlib: extension "XFree86-DRI" missing on display ":0.0".
WARNING: ALC_EXT_capture is subject to change!
[/QUOTE]

got this error today, after that large xfree patch on warty. I fixed it by reinstalling my nvidia drivers, I did this using the installer from the site... so i dunno if warty/hoarys debs will have the same effect.

---

