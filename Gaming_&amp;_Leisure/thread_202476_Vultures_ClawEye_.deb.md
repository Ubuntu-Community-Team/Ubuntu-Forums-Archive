---
title: "Vultures Claw/Eye .deb?"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by ironfistchamp on 2006-06-23
Is there or can someone make a .deb for Vultures Claw or Eye. I can't get the damn thing installed. I tried to download the source but didn't have a clue what to do. The instructions weren't too great. Something about symlinks. I am still a Linux n00b I'm afraid. Yeh so anyway I tried the script and got 

Building and installing Slash'EM in /home/dstamp/vultures/vulturesclawdir
vultures_gfl.c: In function ‘vultures_load_surface’:
vultures_gfl.c:62: warning: pointer targets in passing argument 1 of ‘png_sig_cmp’ differ in signedness
make[2]: yacc: Command not found
make[2]: *** [dgn_yacc.c] Error 127
make[1]: *** [dungeon] Error 2
make: *** [slashem-home] Error 2

Sooo can anyone help?

Thanks

Ironfistchamp

---

### Post by lark on 2006-06-29
That is *exactly* the message I was getting.  I finally gave up.

What finally worked was to download the .rpm of Vulture's 2.0.0, then convert it using alien.

---

### Post by ironfistchamp on 2006-06-29
Smart idea there. I may try it but I installed it on Windows and played. I don't think it is worth all the trouble really.

---

### Post by DirtDawg on 2006-08-25
> **ironfistchamp said:**
> Is there or can someone make a .deb for Vultures Claw or Eye. I can't get the damn thing installed. I tried to download the source but didn't have a clue what to do. The instructions weren't too great. Something about symlinks. I am still a Linux n00b I'm afraid. Yeh so anyway I tried the script and got 

Building and installing Slash'EM in /home/dstamp/vultures/vulturesclawdir
vultures_gfl.c: In function ‘vultures_load_surface’:
vultures_gfl.c:62: warning: pointer targets in passing argument 1 of ‘png_sig_cmp’ differ in signedness
make[2]: yacc: Command not found
make[2]: *** [dgn_yacc.c] Error 127
make[1]: *** [dungeon] Error 2
make: *** [slashem-home] Error 2

Sooo can anyone help?

Thanks

Ironfistchamp

I too get *exactly* the same errors. I also tried compiling from source, but ended up with more errors.

---

### Post by DirtDawg on 2006-08-25
For the curious, here's what I did to get Vulture's eye working (using Charlieg's suggestions from [this]("http://www.ubuntuforums.org/showthread.php?t=170918&highlight=vultures+eye") thread).

Download a version 2.0 rpm package from [the website]("http://old.darkarts.co.za/projects/vultures/downloads/") (I chose nethack-vultures-2.0.0-3.fc4.i386.rpm, but I'm not sure it matters which one you choose).

Make sure "**alien**" is installed through synaptic.

Open terminal and navigate to whever you stored the rpm file.

Enter: ```
sudo alien NAME-OF-THE-RPM.rpm
``` This will create a 'deb' file from the rpm. Then enter:
```
sudo dpkg -i NAME-OF-THE-DEB.deb
```

It works great!

---

### Post by ironfistchamp on 2006-08-26
Sweet I shall try it out. Thanks

---

### Post by Tharquil on 2007-01-10
Here's instructions to install the newest (2.1.0) version.
[http://www.ubuntuforums.com/showthread.php?t=335262](http://www.ubuntuforums.com/showthread.php?t=335262)

---

### Post by Pnin on 2007-02-26
Sorry Tharquil, but your link doesn't seem to be working. I get

*** ATTENTION ***
You have reached a redirect for ubuntuforums.org
Please click the following link to proceed to the official Ubuntu Forums. ubuntuforums.org

I will try searching, but if anyone has the right pointer it would be much appreciated. It's been months trying to get this pesky timewaster...

---

### Post by Tesiph on 2007-02-26
Well, the error message says you are missing 'yacc'. So maybe you should install it:

```

sudo aptitude install byacc

```

---

### Post by truevox on 2007-11-24
I'm fairly new to anything but the simplest linuxy thing, but it mentions specifically that he has a repository on [his website]("http://www.darkarts.co.za/project/vultures/"):

> Together, I refer to them as Vulture's. If you download any file in source form, or **from the repository** you will be downloading both unless explicitly othewise specified.

Doesn't that mean that there's something we can plug into synaptic that will let us get a proper version? Either way, I can't seem to locate the fabled repo, but still... shouldn't that do the trick? Or is it only a Redhat repo (do they make Redhat repos or are they a strictly Debian sorta thing?

Sorry for sounding.... n00bish. As I said, my experience is lacking.

---

### Post by truevox on 2007-11-24
Oh, and for the record, I just tried to "alienize" the rpm. The produced .deb installed just fine (as far as I could tell) but when I tried to run it it started then just as quickly exited. I then tried to launch it via console, and out popped this error:

```
:~$ vultureseye
ERROR: could not open log file vultures_log.txt for appending: Permission denied
[/usr/games/vultureseye/vultureseye]: Program initialization has failed.
Program initialization has failed.
ERROR: could not open log file vultures_log.txt for appending: Permission denied
[/usr/games/vultureseye/vultureseye]: Report error to "games".
Report error to "games".
ERROR: could not open log file vultures_log.txt for appending: Permission denied
[/usr/games/vultureseye/vultureseye]: FATAL: Actual size of gametiles.bin does not match the expected size!
Are you sure you are using the gametiles.bin that was built together with this executable?

FATAL: Actual size of gametiles.bin does not match the expected size!
Are you sure you are using the gametiles.bin that was built together with this executable?


```

So.... this happen to anyone else?

EDIT: Wow. I'm sorry. I just found the "Post Date" field here and.... yeah. Sorry for resurrecting an ancient thread. Once again: Me <-- n00b.

---

### Post by DirtDawg on 2007-11-24
> **truevox said:**
> Oh, and for the record, I just tried to "alienize" the rpm. The produced .deb installed just fine (as far as I could tell) but when I tried to run it it started then just as quickly exited. I then tried to launch it via console, and out popped this error:

So.... this happen to anyone else?

EDIT: Wow. I'm sorry. I just found the "Post Date" field here and.... yeah. Sorry for resurrecting an ancient thread. Once again: Me <-- n00b.

No problem. There's a [howto page on ubuntugeek.com]("http://www.ubuntugeek.com/how-to-install-vultures-isometric-graphics-in-ubuntu.html") that has step by step instructions that work perfectly. You can download the latest version of Vultures from [Dark Arts Studio]("http://www.darkarts.co.za/project/vultures/download") if the howto does not feature the most recent.

Have fun!

---

