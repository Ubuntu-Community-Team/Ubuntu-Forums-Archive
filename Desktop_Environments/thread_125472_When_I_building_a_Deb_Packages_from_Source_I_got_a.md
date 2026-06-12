---
title: "When I building a Deb Packages from Source I got a Error"
date: 2006-02-04
forum: Desktop Environments
---

### Post by grus777 on 2006-02-04
Sorry I move it to 
[http://www.ubuntuforums.org/showthread.php?p=705207#post705207](http://www.ubuntuforums.org/showthread.php?p=705207#post705207)

Please help

When I running dh_make command

I got this error:
[COLOR="Red"]Source file is a bz2 but bzip2 or gzip not available at /usr/bin/dh_make line 409, <STDIN> line 2.[/COLOR] [COLOR="Cyan"]<--what would this mean[/COLOR]



I already check, I had bzip2 installed.

Thank you

---

### Post by dcstar on 2006-02-04
[QUOTE=grus777]Please help

When I running dh_make command

I got this error:
[COLOR="Red"]Source file is a bz2 but bzip2 or gzip not available at /usr/bin/dh_make line 409, <STDIN> line 2.[/COLOR] [COLOR="Cyan"]<--what would this mean[/COLOR]



I already check, I had bzip2 installed.

Thank you[/QUOTE]
What does "whereis bzip2" & "whereis "bunzip2" say?

---

### Post by grus777 on 2006-02-04
[QUOTE=dcstar]What does "whereis bzip2" & "whereis "bunzip2" say?[/QUOTE]

Thank you so much for you replay.

It show

bzip2: /usr/bin/bzip2 /usr/bin/X11/bzip2 /usr/share/man/man1/bzip2.1.gz

and 

bunzip2: /usr/bin/bunzip2 /usr/bin/X11/bunzip2 /usr/share/man/man1/bunzip2.1.gz

---

### Post by cutOff on 2006-02-04
Do you run dh_make command as root? Would you explain what method you use for building deb packages?

---

### Post by grus777 on 2006-02-04
Thank You so much for you help.

I find my solution already.

---

