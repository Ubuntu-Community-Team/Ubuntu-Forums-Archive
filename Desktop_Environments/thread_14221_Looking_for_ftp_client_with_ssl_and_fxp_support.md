---
title: "Looking for ftp client with ssl and fxp support"
date: 2005-02-05
forum: Desktop Environments
---

### Post by rust on 2005-02-05
Read topic :P

any recommendations?

---

### Post by DJ_Max on 2005-02-05
[http://gftp.seul.org/](http://gftp.seul.org/)

---

### Post by rust on 2005-02-05
[QUOTE=DJ_Max][http://gftp.seul.org/](http://gftp.seul.org/)[/QUOTE]
 It looks like a nice ftp client...but for some reason i cant connect with ssl, I get this message:

"FTPS Support unavailable since SSL support was not compiled in. Aborting connection."

Is there an easy fix availible? I tried compiling it myself from the source but got the same thing...something is missing i guess.

---

### Post by DJ_Max on 2005-02-06
[QUOTE=rust]It looks like a nice ftp client...but for some reason i cant connect with ssl, I get this message:

"FTPS Support unavailable since SSL support was not compiled in. Aborting connection."

Is there an easy fix availible? I tried compiling it myself from the source but got the same thing...something is missing i guess.[/QUOTE]
I haven't downloaded it yet, but there should be some ./configure --ARGUMENTS available to use SSL support. Look in the INSTALL or README file(s).

---

### Post by Devi0s on 2005-07-13
Looks like Ubuntu packagers left out ftps support in gftp and in lftp, and attempting to install ftp-ssl results in ubuntu-base being removed for some reason.

Similar thread: [http://ubuntuforums.org/showthread.php?t=5376](http://ubuntuforums.org/showthread.php?t=5376)

I submitted the following:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=12671](https://bugzilla.ubuntu.com/show_bug.cgi?id=12671) (gftp)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=12672](https://bugzilla.ubuntu.com/show_bug.cgi?id=12672) (lftp)

---

### Post by msh on 2005-07-19
konquorer if you need a gui, else ncftp.

---

### Post by msh on 2005-07-19
konquorer if you need a gui, else ncftp.

---

### Post by xplode_me on 2006-03-22
[http://jfxp.sourceforge.net/](http://jfxp.sourceforge.net/)

Not a very good GUI, but active project, and it WORKS! :)

---

