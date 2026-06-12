---
title: "Gosmose - sega emulator frontend"
date: 2008-04-13
forum: Gaming &amp; Leisure
---

### Post by zagieman on 2008-04-13
Decided to give it it's own thread.

It's a Gtk frontend for the osmose master system emulator.
I made a couple of changes to it, now it remembers the settings from when you last opened it, remembers the last played ROM and the directory your ROMs are stored in.

Would appreciate anyone testing it.

EDIT: File download on page 2

Link for non-members:

[http://www.sendspace.com/file/hzbisj](http://www.sendspace.com/file/hzbisj)

---

### Post by GSZX1337 on 2008-04-16
Tried this on my Ubuntu Lappy. Works great! :)

---

### Post by zagieman on 2008-04-17
Added a bunch more options and packed it together with osmose.

EDIT: New version down the page.

---

### Post by GSZX1337 on 2008-04-23
For those using Ubuntu 64-bit, be sure to use [getlibs]("http://ubuntuforums.org/showthread.php?t=474790").

---

### Post by zagieman on 2008-04-23
GSZX: Try doing a 

```
chmod +x osmose
```

to make sure that osmose is executable.

---

### Post by GSZX1337 on 2008-04-24
Didn't work. :(

---

### Post by zagieman on 2008-04-24
When you run GOsmose in the terminal then run a rom it should output the command it runs to open osmose. Can you post that command?

---

### Post by zagieman on 2008-04-25
Ok so running it from the menu will not work because it needs to be run from the directory that osmose is in because i haven't hard coded its path in GOsmose. So right now it only works double clicking the file or running from the osmose path in the terminal.

This could be fixed by packaging I guess but im not sure how to make a package.

When you run a file from a launcher what directory is it run in? Home?

---

### Post by GSZX1337 on 2008-04-25
I have a separate for my emualtors and ROMs called "Emulation" in Home.

---

### Post by zagieman on 2008-05-01
I have added a very simple shell script inside the tar. This installs gosmose to /usr/bin and ~/.GOsmose so now you can run it with:

```
gosmose
```

To install just navigate to the extracted directory then run:

```
sh install.sh
```

Now making shortcuts should work!

---

### Post by zagieman on 2008-05-05
Ok new install script adds gosmose to the applications menu under games. Also has an uninstall script.


To install:
```
sh install.sh
```

To uninstall:
```
sh uninstall.sh
```

Now all it needs is an icon. Anyone?:)

EDIT:Newest version further down.

---

### Post by GSZX1337 on 2008-06-01
Bump.

Sorry I lost track of this thread. I tried out the latest version of GOsmose, it installs into the games section fine, but when I run it, the FPS drops down to zero. It isn't Osmose, I ran it through the terminal and it runs the games fine.

---

### Post by zagieman on 2008-06-03
Strange, I'll look into it. I guess it is something to do with running the system command in the code. It freezes the frontend until osmose is terminated. Probably not the best way of doing it.

---

### Post by zagieman on 2008-06-05
Ok the only thing I could come up with is the fact that the frontend freezes while osmose opens. Fixed that now but if that doesn't work then it might be some funky 64bit issue which I have no idea about.

Also put an Alex Kidd icon with it. Cheers GSZX.

---

### Post by dragonneus on 2008-06-06
DUDE!!! you totally rock, Ive been looking for a gui emulator for SMS for a long time now, Thank you so much!

---

### Post by GSZX1337 on 2008-07-09
I haven't been in Ubuntu lately since I'm learning ActionScript and Flash isn't available for Linux. As soon asI get a chance to boot back into Ubuntu I'll definitely try this out.

---

### Post by zagieman on 2008-07-15
Link for non-members:

[http://www.sendspace.com/file/hzbisj](http://www.sendspace.com/file/hzbisj)

---

### Post by Wrystyle on 2010-06-16
> **zagieman said:**
> Link for non-members:

[http://www.sendspace.com/file/hzbisj](http://www.sendspace.com/file/hzbisj)
This link no longer works, but it seems I'm a couple of years behind you all!!
Just signed up and downloaded it easy enough.
Nice GUI man simple quick and easy.
Typing in long weird rom names into the CL was a headache!

P.S. Is there a newer version perchance?

---

